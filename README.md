# 🚀 Guía de Comandos Git & GitHub para Django

Esta guía contiene los comandos esenciales para gestionar este proyecto, desde el control de versiones local hasta el despliegue en la nube.

---

## 📂 1. Configuración Inicial e Inspección
Comandos para saber dónde estás parado y configurar tu entorno.

* `git init`: Inicializa un nuevo repositorio local de Git en la carpeta actual.
* `git status`: Muestra el estado actual de tu directorio de trabajo (qué archivos han cambiado, cuáles están listos para subir).
* `git remote -v`: Muestra la URL del repositorio remoto (GitHub) al que estás conectado.
* `git config --list`: Muestra toda la configuración de Git en tu equipo.

---

## 🛠️ 2. El Ciclo de Trabajo Diario
Estos son los comandos que usarás el 90% del tiempo.

| Comando | Descripción |
| :--- | :--- |
| `git add .` | Prepara **todos** los archivos modificados para el siguiente commit. |
| `git add nombre_archivo.py` | Prepara solo un archivo específico. |
| `git commit -m "mensaje"` | Crea una "foto" de tus cambios con un mensaje descriptivo. |
| `git push origin main` | Envía tus commits locales a la rama principal en GitHub. |
| `git pull origin main` | Trae los cambios más recientes desde GitHub a tu PC (útil si trabajas en dos laptops). |

---

## 🌿 3. Ramas (Branches)
Ideales para probar funciones nuevas sin romper la versión que ya funciona.

* `git branch`: Lista todas las ramas locales.
* `git checkout -b nombre-rama`: Crea una rama nueva y te cambia a ella automáticamente.
* `git checkout main`: Regresa a la rama principal.
* `git merge nombre-rama`: Une los cambios de una rama secundaria a la rama donde estás parado.

---

## ⚡ 4. Comandos Especiales para este Proyecto (Vercel/Supabase)
Comandos clave para cuando hagas cambios en la base de datos o el despliegue.

* **Cambiar el Repositorio Remoto:**
    `git remote set-url origin https://github.com/usuario/repo.git`
    *(Útil si decides mover el proyecto a otra cuenta).*

* **Deshacer el último commit (manteniendo tus archivos):**
    `git reset --soft HEAD~1`
    *(Útil si hiciste un commit y olvidaste agregar algo).*

* **Limpiar archivos temporales de Python antes de subir:**
    `find . -name "*.pyc" -delete` o simplemente confía en tu `.gitignore`.

---

## 📝 5. Flujo Recomendado para subir cambios a Vercel
Vercel despliega automáticamente cada vez que haces un `push`. El flujo ideal es:

1. `python manage.py makemigrations` (Si cambiaste modelos).
2. `python manage.py migrate` (Para actualizar tu Supabase).
3. `git add .`
4. `git commit -m "Explicación del cambio"`
5. `git push origin main`

---
> **Tip Pro:** Siempre revisa tu archivo `.env` y asegúrate de que esté en el `.gitignore`. ¡Nunca subas tus contraseñas de Supabase a GitHub!