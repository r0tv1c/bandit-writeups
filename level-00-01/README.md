# Bandit Level 0 → 1

## Objetivo

Acceder al servidor remoto mediante SSH y obtener la contraseña del siguiente nivel desde un archivo disponible.

---

## Enumeración

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

## Ejecución

```bash
bandit0@bandit:~$ cat readme
```

---

## Resultado

Se obtiene la contraseña del siguiente nivel
🔒 *Contraseña omitida por cumplimiento de reglas de OverTheWire*

---

## Explicación técnica

* `ssh` permite conexión remota cifrada
* `-p 2220` especifica puerto
* `ls` lista archivos
* `cat` muestra contenido

---

## Nota de atacante

El acceso inicial permite:

* Reconocimiento del sistema
* Identificación de archivos sensibles
* Evaluación del entorno

---

## Lección clave

La conexión remota segura es fundamental en:

* Pentesting
* Administración de sistemas
* Entornos Linux

---

## Referencias

* OverTheWire Bandit
