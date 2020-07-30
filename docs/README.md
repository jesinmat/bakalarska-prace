## Vygenerování PDF s prací

Vygenerovaná PDF jsou dostupná u jednotlivých commitů jako Build Artifacts.
Pokud chcete přesto vygenerovat PDF sami, níže je uveden návod pro Ubuntu/Debian.

```shell
sudo apt install -y biber default-jre lmodern python-pip texlive texlive-bibtex-extra texlive-extra-utils texlive-generic-extra texlive-lang-czechslovak texlive-xetex

python -m pip install -U pygments 

git clone https://github.com/jesinmat/bakalarska-prace.git

cd bakalarska-prace

arara BP_Jesina_Matyas_2020.tex
```

## Sestavení obrazu systému

Tento návod popisuje potřebné kroky k sestavení obrazu systému.
Pro sestavení byl využit TKLDev 16.0, základ systému Debian Buster.
V případě použití novější verze nahraďte odpovídající příkazy.

### Formát .iso

1. Stáhněte a spusťte [TKLDev](https://www.turnkeylinux.org/tkldev) jako lokální virtuální stroj.
2. Proveďte úvodní nastavení podle průvodce. Zálohování a zasílání upozornění je možné přeskočit.
3. Přihlaste se do systému pomocí SSH na účet `root` zvoleným heslem.
4. Ujistěte se, že byly staženy potřebné soubory spuštěním příkazu `tkldev-setup`.
4. Stáhněte repozitář s GameServer soubory do složky `/turnkey/fab/products/gameserver`:
    ```shell
    git clone https://github.com/jesinmat/tkl-gameserver /turnkey/fab/products/gameserver
    ```
5. Vytvořte obraz systému příkazem `make`:
    ```shell
    cd /turnkey/fab/products/gameserver
    make
    ```
6. Vytvoiřený obraz je k dispozici v  `/turnkey/fab/products/gameserver/build/product.iso`

### Ostatní formáty

Tento návod slouží k převodu instalačního obrazu ve formátu `.iso` na ostatní formáty. Návod popisuje vytvoření `.qcow2` obrazu pro OpenStack, v případě
jiné platformy je postup obdobný.

1. Zvolte výchozí konfigurací pomocí následujících příkazů:
    ```shell
    cd /turnkey/buildtasks
    cp -r config.example/ config
    ```
2. Zkopírujte dříve vytvořený `.iso` obraz do složky s obrazy. V případě použití
novější systému verze upravte název souboru.
    ```shell
    cp /turnkey/fab/products/gameserver/build/product.iso /mnt/isos/turnkey-gameserver-16.0-buster-amd64.iso
    ```
3. Vytvořte hash obrazu.
    ```shell
    ./bin/generate-signature /mnt/isos/turnkey-gameserver-16.0-buster-amd64.iso
    ```
4. V době psaní textu je v systému `buildtasks` chybně umístěná složka, která zabraňuje
vytvoření obrazu. Pro sestavení obrazu je nutné složku přemístit.
    ```shell
    cp -r patches/openstack/overlay/lib/* patches/openstack/overlay/usr/lib/
    rm -r patches/openstack/overlay/lib/
    ```
5. Vytvořte požadovaný formát obrazu.
    ```shell
    ./bt-openstack gameserver-16.0-buster-amd64
    ```
6. Vytvořený obraz je k dispozici v `/mnt/builds/openstack/turnkey-gameserver-16.0-buster-amd64-openstack.qcow2`
