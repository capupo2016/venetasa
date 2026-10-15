# Guia: publicar VeneTasa fuera de Google Play (en español)

Este paquete contiene: la página de descarga (index.html), el README y esta guía.

## 1) Verificación Google / registro (evitar bloqueos 2026-2027)

Para compartir con amigos (< 20 dispositivos), lo ideal y gratis es **Limited distribution account** (no pide cédula/ID gubernamental).

### Requisitos
- Cuenta Google
- 2-Step verification activado
- Perfil de pagos de Google vinculado
- Correo de contacto

### Pasos
1. [android.google.com/developerconsole/developers](https://android.google.com/developerconsole/developers) → Crea "Limited distribution account"
2. Completa datos y vincula perfil de pagos
3. "Packages" → registra com.capupo2016.venetasa
4. Introduce la huella SHA-256:

   $sha

5. Sube el APK firmado con esa clave cuando te lo pida (prueba de propiedad)
6. Espera hasta que aparezca "Registered"

**Notas:** Protecciones inician 30 sep 2026 (BR, ID, SG, TH), luego global 2027. Tus amigos deben activar "Instalar apps de origen desconocido".

## 2) Clave de firma para distribución
El APK actual usa **debug.keystore** (genérico). Para publicación correcta, crea una **release keystore**.

Comando (ajusta contraseñas):
`	ext
keytool -genkey -v -keystore veneTasa-release.keystore -alias veneTasa -keyalg RSA -keysize 2048 -validity 10000
`

**Importante:** al cambiar de keystore, el teléfono que ya tiene 1.0.3 debe desinstalar e instalar el nuevo APK (se pierden datos). Si nadie más lo tiene instalado, este es el momento.

## 3) GitHub + Página de descarga
1. Crea repo público en GitHub: enetasa
2. Sube index.html, README.md, GUIA-PUBLICAR.md a ese repo
3. Crea un Release (1.0.3) → adjunta VeneTasa.apk
4. Settings → Pages → servir desde main (root)
5. La página detectará automáticamente el APK del último release.
