# gitHub-settings

## Git configuration
### Resumen de los pasos para configurar Git en un entorno Windows

1. **Descargar e instalar Git**  
   - Visita el sitio oficial de Git: [https://git-scm.com/](https://git-scm.com/)  
   - Descarga el instalador para Windows.  
   - Durante la instalación, elige las configuraciones predeterminadas, a menos que tengas preferencias específicas.

2. **Verificar la instalación**  
   - Abre la terminal de Windows o PowerShell.  
   - Escribe el comando para verificar la versión instalada:  
     ```bash
     git --version
     ```  
   - Debe mostrar la versión instalada de Git.

3. **Configurar nombre de usuario y correo electrónico global**  
   - Establece tu nombre de usuario:  
     ```bash
     git config --global user.name "Tu Nombre"
     ```  
   - Configura tu correo electrónico:  
     ```bash
     git config --global user.email "tu_email@example.com"
     ```  
   - Verifica la configuración:  
     ```bash
     git config --list
     ```

4. **Configurar el editor predeterminado (opcional)**  
   - Si deseas usar un editor de texto diferente (por ejemplo, VS Code), configúralo:  
     ```bash
     git config --global core.editor "code --wait"
     ```

5. **Generar y configurar una clave SSH (para GitHub, GitLab, etc.)**  
   - Genera una clave SSH:  
     ```bash
     ssh-keygen -t ed25519 -C "tu_email@example.com"
     ```  
   - Sigue las instrucciones y guarda la clave en la ubicación predeterminada.  
   - Añade la clave SSH a tu cuenta de GitHub o GitLab:  
     - [Instrucciones para GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)  
     - [Instrucciones para GitLab](https://docs.gitlab.com/ee/ssh/)

6. **Probar la conexión SSH (si configuraste una clave)**  
   - Verifica que la conexión sea exitosa:  
     ```bash
     ssh -T git@github.com
     ```  
   - Si usas GitLab, cambia la URL a:  
     ```bash
     ssh -T git@gitlab.com
     ```

7. **Configurar el gestor de credenciales**  
   - Durante la instalación, puedes seleccionar el gestor de credenciales de Windows para almacenar tus credenciales de forma segura.  
   - Si no lo hiciste durante la instalación, puedes configurarlo con:  
     ```bash
     git config --global credential.helper wincred
     ```

8. **Opcional: Instalar una interfaz gráfica para Git**  
   - Si prefieres usar una interfaz gráfica, puedes instalar herramientas como:  
     - [GitHub Desktop](https://desktop.github.com/)  
     - [Sourcetree](https://www.sourcetreeapp.com/)  

9. **Clonar o inicializar un repositorio para probar la configuración**  
   - Clonar un repositorio existente:  
     ```bash
     git clone <url_del_repositorio>
     ```  
   - Crear un nuevo repositorio:  
     ```bash
     git init
     ```

10. **Actualizar Git regularmente**  
    - Verifica actualizaciones en el sitio oficial: [https://git-scm.com/](https://git-scm.com/).


---

## Basic Git Commands

### Initializing and Cloning Repositories

- **`git init`**  
  Initializes a new Git repository in the current directory.  
  Example:  
  ```bash
  git init
  ```

- **`git clone <repository_url>`**  
  Clones an existing repository to your local machine.  
  Example:  
  ```bash
  git clone https://github.com/user/repo.git
  ```

---

### Adding and Committing Changes

- **`git add <file>`**  
  Stages changes in the specified file for the next commit.  
  Example:  
  ```bash
  git add file.txt
  ```

- **`git commit -m "<message>"`**  
  Commits the staged changes with a descriptive message.  
  Example:  
  ```bash
  git commit -m "Initial commit"
  ```

- **`git add . && git commit -m "<message>"`**  
  Stages all changes and commits them with a message.  
  Example:  
  ```bash
  git add . && git commit -m "Updated project files"
  ```

---

### Checking Status and Logs

- **`git status`**  
  Shows the status of your working directory and staging area.  
  Example:  
  ```bash
  git status
  ```

- **`git log`**  
  Displays the commit history of the repository.  
  Example:  
  ```bash
  git log
  ```

---

### Working with Branches

- **`git branch`**  
  Lists all branches and highlights the current one.  
  Example:  
  ```bash
  git branch
  ```

- **`git branch <branch_name>`**  
  Creates a new branch with the specified name.  


--

## Cómo usar ramas y dar nombres correctos a ramas y commits

Trabajar con ramas en Git es fundamental para mantener un flujo de trabajo limpio y organizado. Aquí te lo explico paso a paso y con buenas prácticas que siguen los desarrolladores profesionales.

---

### **¿Qué son las ramas en Git?**
Las ramas en Git son versiones independientes de tu código en las que puedes trabajar sin afectar la rama principal (generalmente llamada `main` o `master`). Cada rama se utiliza para trabajar en características, correcciones o experimentos específicos.

---

### **¿Por qué usar ramas?**
1. **Separación de tareas**: Cada rama está asociada a una tarea específica (feature, bug fix, hotfix, etc.).
2. **Colaboración**: Diferentes desarrolladores pueden trabajar simultáneamente en ramas separadas sin conflictos.
3. **Control de versiones**: Puedes experimentar sin temor a romper el código principal.

---

### **Buenas prácticas al nombrar ramas**
Los nombres de las ramas deben ser claros, descriptivos y reflejar el propósito de la tarea. Sigue estas convenciones comunes:

1. **Convención general**: 
   ```
   tipo/nombre-tarea
   ```
   Ejemplo:
   - `feature/nueva-funcionalidad`
   - `bugfix/arreglo-error-login`
   - `hotfix/actualizacion-urgente`

2. **Tipos de ramas comunes**:
   - **`feature/`**: Para nuevas funcionalidades o mejoras.  
     Ejemplo: `feature/agregar-busqueda`.
   - **`bugfix/`**: Para correcciones de errores.  
     Ejemplo: `bugfix/corregir-registro`.
   - **`hotfix/`**: Para cambios urgentes en producción.  
     Ejemplo: `hotfix/corregir-error-produccion`.
   - **`release/`**: Para preparar lanzamientos.  
     Ejemplo: `release/v1.2.0`.
   - **`chore/`**: Para tareas menores o de mantenimiento.  
     Ejemplo: `chore/actualizar-dependencias`.

3. **Consideraciones adicionales**:
   - Usa **kebab-case** para separar palabras: `nombre-descriptivo`.
   - Incluye identificadores de tareas si usas herramientas como Jira o Trello.  
     Ejemplo: `feature/JIRA-1234-login`.

---

### **Cómo trabajar con ramas en Git**

#### 1. **Crear una nueva rama**
   ```bash
   git checkout -b feature/nombre-rama
   ```
   Esto crea y cambia a la nueva rama.

#### 2. **Ver todas las ramas**
   ```bash
   git branch
   ```
   Muestra las ramas locales. Usa `git branch -a` para ver también las ramas remotas.

#### 3. **Cambiar de rama**
   ```bash
   git checkout nombre-rama
   ```

#### 4. **Subir una rama al repositorio remoto**
   ```bash
   git push -u origin nombre-rama
   ```

#### 5. **Fusionar una rama con `main`**
   Cambia a la rama `main` y luego fusiónala:
   ```bash
   git checkout main
   git merge nombre-rama
   ```

#### 6. **Eliminar una rama**
   - Local:
     ```bash
     git branch -d nombre-rama
     ```
   - Remoto:
     ```bash
     git push origin --delete nombre-rama
     ```

---

### **Buenas prácticas para escribir mensajes de commit**

Un buen mensaje de commit debe ser claro y descriptivo. Sigue estas reglas:

1. **Estructura general**:
   ```
   tipo: breve-descripcion

   Explicación opcional más detallada.
   ```

2. **Tipos de commits más comunes**:
   - **`feat:`**: Para agregar nuevas funcionalidades.  
     Ejemplo: `feat: agregar validación al formulario de login`
   - **`fix:`**: Para corregir errores.  
     Ejemplo: `fix: corregir error en la navegación móvil`
   - **`docs:`**: Para cambios en documentación.  
     Ejemplo: `docs: actualizar README con nuevas instrucciones`
   - **`style:`**: Para cambios de formato o estilo que no afectan la lógica.  
     Ejemplo: `style: aplicar prettier al código`
   - **`refactor:`**: Para reestructuración de código sin cambiar su comportamiento.  
     Ejemplo: `refactor: simplificar función de cálculo`
   - **`test:`**: Para agregar o actualizar pruebas.  
     Ejemplo: `test: agregar pruebas para validación de correo`
   - **`chore:`**: Para tareas menores o mantenimiento.  
     Ejemplo: `chore: actualizar dependencias`

3. **Ejemplo completo**:
   ```
   feat: agregar funcionalidad de búsqueda avanzada

   - Implementar el backend para búsqueda avanzada.
   - Actualizar la interfaz de usuario con nuevos filtros.
   - Agregar pruebas unitarias para garantizar funcionalidad.
   ```

---

### **Consejos finales para un flujo de trabajo profesional**
1. **Mantén tus ramas pequeñas y enfocadas en una sola tarea**. Esto facilita las revisiones y reduce conflictos.
2. **Revisa tus cambios antes de hacer un commit**:
   ```bash
   git diff
   ```
3. **Sincroniza tus ramas regularmente con la rama principal para evitar conflictos grandes**:
   ```bash
   git pull origin main
   ```
4. **Usa herramientas de revisión de código como Pull Requests o Merge Requests para garantizar calidad**.

Siguiendo estas prácticas, tu flujo de trabajo será más organizado y profesional. ¡Siempre prioriza la claridad en tus ramas y commits para facilitar la colaboración!
