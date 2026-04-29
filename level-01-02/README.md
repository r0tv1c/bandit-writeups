# 🧪 Bandit Level 1 → 2

## 🎯 Objetivo

Acceder al servidor remoto mediante SSH y obtener la contraseña del siguiente nivel desde un archivo con nombre especial.

---

## 🔍 Enumeración

Conexión al servidor:

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

Listado de archivos:

```bash
bandit1@bandit:~$ ls
-
```

---

## 🧩 Problema

Identificamos al archivo en la fase de enumeración. El archivo se llama `-`, lo cual entra en conflicto con la sintaxis de comandos, `-` se interpreta comúnmente como un argumento o flag.

---

## ⚙️ Ejecución

Utilizamos la ruta relativa del archivo.

```bash
bandit1@bandit:~$ cat ./- 
```

---

## 🔑 Resultado

Se obtiene la contraseña del siguiente nivel
🔒 *Contraseña omitida por cumplimiento de reglas de OverTheWire*
---

## 🧠 Explicación técnica

* `ssh` (Secure Shell) establece una conexión remota cifrada entre cliente y servidor
* `-p 2220` especifica el puerto del servicio
* `ls` lista los archivos en el directorio actual
* `cat` muestra el contenido de un archivo en la terminal
* Ruta relativa: respecto al directorio actual (.)
* Ruta absoluta: desde la raíz (/)

---

## 🔥 Nota de atacante

El uso de nombres de archivos con caracteres especiales puede emplearse para:

- Evadir herramientas automatizadas  
- Romper scripts mal diseñados  
- Generar ambigüedad en la interpretación de comandos
- Posible vector de evasión en scripts automatizados que no sanitizan inputs

---

## 🛠 Troubleshooting

| Problema          | Causa                    | Solución                   |
| ----------------- | ------------------------ | -------------------------- |
| No conecta        | Puerto incorrecto        | Usar `-p 2220`             |
| Acceso denegado   | Credenciales incorrectas | Verificar usuario/password |
| SSH no disponible | Cliente no instalado     | Instalar OpenSSH           |
| `cat -` No funciona | Interpretado como flag | Usar ./- |

---

## 📚 Lección clave

El acceso remoto seguro es fundamental en:

* Pentesting
* Administración de sistemas
* Operación en entornos Linux

---

## 🔗 Referencias

* OverTheWire Bandit
* Manual de `ssh`
