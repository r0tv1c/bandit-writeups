# 🧪 Bandit Level 5 → 6

## 🎯 Objetivo

Acceder al servidor remoto mediante SSH y obtener la contraseña del siguiente nivel alojada en algún directorio de `inhere`.

---

## 🔍 Enumeración

Conexión al servidor:

```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
```

Listado de archivos:

```bash
bandit5@bandit:~$ ls
inhere
```

```bash
bandit5@bandit:~$ ls inhere/
maybehere00  maybehere04  maybehere08  maybehere12  maybehere16
maybehere01  maybehere05  maybehere09  maybehere13  maybehere17
maybehere02  maybehere06  maybehere10  maybehere14  maybehere18
maybehere03  maybehere07  maybehere11  maybehere15  maybehere19
```

---

## 🧩 Problema

Existe una gran cantidad de archivos distribuidos en múltiples directorios, es necesario filtrar mediante características específicas (tamaño, tipo y permisos).

---

## ⚙️ Ejecución

Se identifica el archivo que cumple con las condiciones del reto.

Condiciones: 
* human-readable
* 1033 bytes in size
* not executable

```bash
# Método simple (menos robusto, puede fallar con múltiples resultados):
bandit5@bandit:~$ file $(find inhere -type f -size 1033c ! -executable)

# Método robusto
bandit5@bandit:~$ find inhere -type f -size 1033c ! -executable -exec file {} \;
```


```bash
bandit5@bandit:~$ cat inhere/maybehereXX/.fileXX
```

---

## 🔑 Resultado

🔒 *Contraseña omitida por cumplimiento de reglas de OverTheWire*
---

## 🧠 Explicación técnica

* `find` permite localizar archivos mediante filtros como tamaño (`-size`), tipo (`-type`) y permisos (`! -executable`)
* `-exec` ejecuta un comando (`file`) sobre cada resultado encontrado

---

## 🔥 Nota de atacante

El uso de herramientas como `find` permite:

- Enumerar archivos sensibles en sistemas comprometidos  
- Localizar credenciales, configuraciones o backups basadas en tamaño, permisos o tipo  
- Automatizar búsquedas en grandes cantidades de archivos  

---

## 🛠 Troubleshooting

| Problema          | Causa                    | Solución                   |
| ----------------- | ------------------------ | -------------------------- |
| No conecta        | Puerto incorrecto        | Usar `-p 2220`             |
| Acceso denegado   | Credenciales incorrectas | Verificar usuario/password |
| SSH no disponible | Cliente no instalado     | Instalar OpenSSH           |
| `find` no devuelve resultados | Filtros incorrectos | Revisar sintaxis y flags |
| Demasiados resultados | Falta de filtros | Agregar `-type f` |

---

## 📚 Lección clave

El uso eficiente de `find` permite realizar enumeración avanzada en sistemas Linux, habilidad clave en pentesting y análisis de sistemas.

---

## 🔗 Referencias

* OverTheWire Bandit
* Manual de `find`
