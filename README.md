# Reubah – Contenedor Docker

Reubah es una herramienta web de código abierto diseñada para procesar imágenes y convertir documentos a través de una interfaz extremadamente sencilla y limpia. Es la solución perfecta para quienes buscan un entorno unificado donde transformar archivos sin complicaciones, aprovechando la potencia de Docker para que funcione en cualquier lugar.


---

## 🚀 Características

- Imagen oficial: `ghcr.io/dendianugerah/reubah:latest`
- Interfaz web sencilla
- Despliegue rápido mediante Docker
- Contenedor endurecido (hardening básico)
- Reinicio automático (`unless-stopped`)

---

## 📁 Estructura de archivos

```text
.
└── compose.yml
```

---

## 🐳 docker-compose.yml

```yaml
services:
  reubah:
    image: ghcr.io/dendianugerah/reubah:latest
    container_name: reubah
    ports:
      - "8081:8081"
    security_opt:
      - no-new-privileges:true
    cap_drop:
      - ALL
    restart: unless-stopped
```

---

## 🔐 Seguridad

Esta configuración aplica un **hardening básico** al contenedor:

- `no-new-privileges:true` → evita escaladas de privilegios
- `cap_drop: ALL` → elimina todas las capacidades Linux innecesarias

Recomendado para exponer Reubah únicamente en redes internas o entornos controlados.

---

## 🌐 Acceso a la interfaz web

```text
http://TU-IP:8081
```

---

## ▶️ Puesta en marcha

```bash
docker compose up -d
```

---

## 🛑 Detener el contenedor

```bash
docker compose down
```

---

## 🔄 Actualizar Reubah

```bash
docker compose pull
docker compose up -d
```

---

## ⚠️ Consideraciones

- No expongas el servicio directamente a Internet sin protección adicional
- Ideal para entornos de pruebas, staging o redes internas
- Compatible con reverse proxies como Nginx, Traefik o Caddy

---



