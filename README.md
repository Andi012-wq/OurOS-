# OurOS#

**OurOS#** është një sistem operativ i ndërtuar nga zero me Linux From Scratch (LFS), projektuar **nga programuesit, për programuesit**. Me fokus vetëm në terminal, OurOS# ofron një ambient minimalist dhe të fuqishëm për zhvillim.

---

## 📦 Përmbajtja e Repo-së

```
OurOS/
├── BUILD.md                # Udhëzime të hollësishme për ndërtim me LFS
├── build.sh                # Skript automatik për përgatitje, kompajlim dhe ISO
├── releases/               # Folder me ISO të ndërtuara (p.sh. OurOS#.iso)
│   └── OurOS#-v1.0.iso     # ISO zyrtare për boot në VM ose USB
├── usr/                    # File-system bazë i ndërtuar (rootfs)
│   ├── bin/                # Binaries kryesore
│   ├── lib/                # Biblioteka
│   └── ...
├── etc/                    # Konfigurime (p.sh. os-release, fstab)
└── README.md               # Ky dokument
```

---

## 🎯 Features Kryesore

- **Shell-Only Environment**: Nuk ka GUI, vetëm një shell për komanda të menjëhershme.
- **Ndërtim nga Zero**: Secila pjesë (toolchain, kernel, coreutils) është kompajluar nga kod burimor.
- **Komanda Custom**:
  - `ourcalc`  — Kalkulator CLI
  - `ourclock` — Orë live në terminal
  - `ouredit`  — Editor i thjeshtë teksti
  - `ourman`   — Manual për komanda OurOS#
  - `ourinfo`  — Informacione sistemi (uptime, disk, CPU)
  - `ourgit`   — Helper për Git
- **Modular**: Shtoni skripta ose binare në `/usr/bin/` dhe bëhen komanda të plota.
- **Open Source**: Kontriboni në GitHub, forkoni, rregulloni, dhe bëni pull requests.

---

## 🚀 Instalimi dhe Boot

### 1. Klononi Repo-n

```bash
git clone https://github.com/YourUser/OurOS.git
cd OurOS
```

### 2. Rishikoni Prerequisitet

- **Linux Host** (Debian/Ubuntu/Arch) me:
  - `bash`, `gcc`, `make`, `binutils`, `grub-pc-bin`, `xorriso`
  - Minimum 20 GB hapësirë
  - Minimum 8 GB RAM

### 3. Përdorni Skriptin `build.sh`

```bash
chmod +x build.sh
./build.sh
```

Skripti:
1. Përgatit mjedisin (folders, variabla)
2. Shkarkon dhe kompajlon toolchain-in
3. Kompajlon kernelin dhe coreutils
4. Ndërton filesystem bazë në `usr/`
5. Gjeneron ISO në `releases/OurOS#-v1.0.iso`

### 4. Boot në VirtualBox / QEMU / USB

- **VirtualBox**:
  1. Krijo VM Linux (64-bit, 1024+ MB RAM).
  2. Vegëzo `releases/OurOS#-v1.0.iso` si CD/DVD.
  3. Start VM → Booton OurOS#.

- **QEMU**:
  ```bash
  qemu-system-x86_64 -m 1024 -cdrom releases/OurOS#-v1.0.iso
  ```

- **USB** (me Rufus/Etcher): Shkruani ISO-n në një USB të varur.

### 5. Hapa Pas-Installim

Pas boot:
```
login: root
password: root    # (ndrysho në BUILD.md pas instalimit)
```
- Ndryshoni `/etc/os-release` për versionin tuaj.
- Eksploroni komandat custom: `ourcalc`, `ourclock`, `ouredit`.

---

## 🛠️ Si të Ndërtoni / Përshtatni

- **BUILD.md** për detaje të plota, përfshi komandat `configure` për secilën paketë.
- Përshtatni `/etc/os-release` për emër, version, dhe URL.
- Shtoni skripta tuaja në `/usr/bin/`:
  ```bash
  sudo cp myscript /usr/bin/mycmd
  sudo chmod +x /usr/bin/mycmd
  ```

---

## 💡 Kontributoni

1. Forkoni projektin në GitHub.
2. Krijoni një branch të re: `git checkout -b feature/my-feature`.
3. Bëni ndryshimet.
4. `git commit -m "Add awesome feature"`.
5. `git push origin feature/my-feature`.
6. Krijoni Pull Request për review.

---

**OurOS#** është në zhvillim të vazhdueshëm—bashkohuni dhe ndihmoni të ndërtojmë sistemin ultimativ për zhvillues!
