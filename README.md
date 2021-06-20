# CAS Overlay Template [![Build Status](https://travis-ci.org/apereo/cas-overlay-template.svg?branch=master)](https://travis-ci.org/apereo/cas-overlay-template)

Cas Overlay ini digunakan sebagai dasar dalam pembuatan SSO dengan CAS

# Versi

- CAS `6.4.x`
- JDK `11`

# Configuration

- Direktori bernama `etc` mengandung file konfigurasi dan direktori yang harus di-copy-kan adalah `/etc/cas/config`.

```bash
./gradlew[.bat] copyCasConfiguration
```

- Untuk build, atur konfigurasi dalam file bernama `gradle.properties` .

## Menambahkan Modul

Modul CAS dispesifikasikan oleh `dependencies` dalam file [Gradle build script](build.gradle):

```gradle
dependencies {
    implmentation "org.apereo.cas:cas-server-some-module:${project.casVersion}"
    ...
}
```

# Deployment

- Buat file keystore dengan nama `thekeystore` di dalam `/etc/cas`. Gunakan password `changeit` untuk keystorenya dan sertifikat. Dapat juga dibuat dengan perintah `keytool` dari JDK, yaitu:

```bash
./gradlew[.bat] createKeystore
```

- Pastikan keystore sudah di-load dengan key dan sertifikat server.

Jika deployment berhasil, silakan cek pada browser dengan URL:

- `https://cas.server.name:8443/cas`

## Dengan Eksekusi WAR

Jalankan CAS Web dengan perintah:

```bash
./gradlew[.bat] run
```

Debug cAS Web:

```bash
./gradlew[.bat] debug
```

Run CAS Web sebagai _standalone_ executable WAR:

```bash
./gradlew[.bat] clean executable
```

## Docker

Berikut merupakan cara deploy CAS menggunakan Docker, baik menggunakan Jib atau Dockerfile.

### Jib

```bash
./gradlew build jibDockerBuild
```

### Dockerfile

Pengaturan Ddckerfile terdapat pada file`Dockerfile`

```bash
chmod +x *.sh
./docker-build.sh
./docker-run.sh
```
