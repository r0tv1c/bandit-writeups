# 🧪 Bandit Level 0 → 1

## 🎯 Objetivo

Acceder al servidor remoto mediante SSH y obtener la contraseña del siguiente nivel desde un archivo disponible.

---

## 🔍 Enumeración

Conexión al servidor:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

Listado de archivos:

```bash
bandit0@bandit:~$ ls
readme
```

---

## 🧩 Problema

Identificar el archivo que contiene la contraseña del siguiente nivel.

---

## ⚙️ Ejecución

```bash
bandit0@bandit:~$ cat readme
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

---

## 🔥 Nota de atacante

El acceso inicial a un sistema permite:

* Enumeración básica del entorno
* Identificación de archivos sensibles
* Evaluación del contexto de usuario

Este paso corresponde a una fase inicial de **post-explotación**.

---

## 🛠 Troubleshooting

| Problema          | Causa                    | Solución                   |
| ----------------- | ------------------------ | -------------------------- |
| No conecta        | Puerto incorrecto        | Usar `-p 2220`             |
| Acceso denegado   | Credenciales incorrectas | Verificar usuario/password |
| SSH no disponible | Cliente no instalado     | Instalar OpenSSH           |

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
