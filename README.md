# 🔓 WordPress XML-RPC Brute Force Tool

![License](https://img.shields.io/badge/license-MIT-red.svg)  
![Bash Version](https://img.shields.io/badge/bash-4.0%2B-green.svg)  
![Status](https://img.shields.io/badge/purpose-Educational%20Only-orange.svg)  
![Status](https://img.shields.io/badge/status-active-success.svg)  

Herramienta educativa en Bash para demostrar vulnerabilidades en el endpoint XML-RPC de WordPress mediante fuerza bruta simple.

> [!WARNING]  
> **SOLO PARA FINES EDUCATIVOS Y TESTING AUTORIZADO**  
> El uso no autorizado es ilegal y los autores no se responsabilizan de un mal uso.

---

## 📋 Tabla de Contenidos

- [🎯 Propósito](#-propósito)  
- [📦 Instalación](#-instalación)  
- [💡 Uso](#-uso)  
- [🔍 Metodología](#-metodología)  
- [🛡️ Mitigaciones](#️-mitigaciones)  
- [🤝 Contribución](#-contribución)  
- [📄 Licencia](#-licencia)  

---

## 🎯 Propósito

- **Aprender XML-RPC**: Entender llamadas `wp.getUsersBlogs`.  
- **Fuerza Bruta Básica**: Iterar wordlist y verificar credenciales.  
- **Concienciación**: Mostrar la importancia de deshabilitar o proteger XML-RPC.

---

## 📦 Instalación

> **Requisitos**  
> - Bash 4.0+  
> - `curl` instalado  
> - Permisos de ejecución  

```bash
git clone https://github.com/victorbelmontee/wp-xmlrpc-bruteforce.git
cd wp-xmlrpc-bruteforce
chmod +x xmlrpc_bruteforce.sh
```

---

## 💡 Uso

```bash
# Definir target en el script (por defecto localhost:31337)
# Ejecutar fuerza bruta con rockyou.txt
./xmlrpc_bruteforce.sh
```

Para cambiar target, edita la URL en la variable `curl` dentro de `createXML()`.

---

## 🔍 Metodología

1. **Construir XML** con `<methodName>wp.getUsersBlogs</methodName>`.
2. **Enviar POST** al `xmlrpc.php`.
3. **Verificar respuesta**: Si no contiene "Incorrect username or password.", se considera éxito.
4. **Iterar wordlist** hasta hallar credenciales válidas o acabar la lista.

---

## 🛡️ Mitigaciones

* **Deshabilitar XML-RPC** en `functions.php`:

  ```php
  add_filter('xmlrpc_enabled', '__return_false');
  ```
* **Bloquear acceso** vía `.htaccess` o firewall.
* **Plugins de seguridad** que limiten intentos o implementen CAPTCHA.

---

## 🤝 Contribución

1. Fork → 2. Branch feature → 3. Commit → 4. PR

---

## 📄 Licencia

MIT. Ver [`LICENSE`](LICENSE) para más detalles.
