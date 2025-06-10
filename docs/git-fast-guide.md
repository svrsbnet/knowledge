# Git Fast guide

···
~/dev/
├── personal/
│   ├── github-usuario/
│   │   ├── containers/
│   │   ├── kubernetes/
│   │   └── python/
│   └── otros/
│       └── proyectos-experimentales/
├── trabajo/
│   ├── gitlab-empresa/
│   │   └── devops/
│   │       ├── ci-cd/
│   │       ├── infra/
│   │       └── monitoring/
│   └── clientes/
│       └── cliente-x/
│           └── proyecto-x/
···

## Git config por cuenta

    [includeIf "gitdir:~/dev/github/personal/"]
      path = ~/.gitconfig-personal

    [includeIf "gitdir:~/dev/gitlab/company/"]
      path = ~/.gitconfig-work

    [user]
      name = Tu Nombre
      email = <tunombre@gmail.com>

    [user]
      name = Tu Nombre Profesional
      email = <tunombre@tuempresa.com>

## Alias rápidos (opcional)

Agrega estos a tu .zshrc si lo deseas:

    alias cdgh="cd ~/dev/github/personal"
    alias cdgl="cd ~/dev/gitlab/company/devops"

## Ubicación del archivo .gitconfig

Archivo global (de usuario):

Se encuentra en tu directorio personal:

    ~/.gitconfig

O en ruta completa:

    /Users/tu-usuario/.gitconfig

Este archivo es el que Git usa para configuraciones de usuario, como nombre, email, alias, color del output, etc.

Archivo local (por proyecto):

Cada repositorio Git también puede tener su propia configuración:

    /path/a/tu/repositorio/.git/config

Este afecta solo a ese repositorio. Git aplica configuraciones en este orden de prioridad:

  1. Local (~/.git/config) — más específico
  2. Global (~/.gitconfig)
  3. Sistema (/etc/gitconfig)

¿Cómo saber cuál estás usando?

Puedes ver tu configuración actual con:

    git config --list --show-origin

Esto te muestra todas las configuraciones activas y de qué archivo vienen.
🛠️ Para editar el .gitconfig global

nano ~/.gitconfig

O si prefieres abrirlo con Visual Studio Code:

code ~/.gitconfig

¿Quieres que te dé un .gitconfig base ya listo con los includeIf para múltiples cuentas?
You said:
Si por favot
ChatGPT said:

Perfecto. Aquí tienes una configuración lista para copiar y pegar, que te permite tener dos perfiles de Git:

    Uno personal (para proyectos en GitHub)

    Otro profesional (para proyectos de tu empresa en GitLab)

📄 1. ~/.gitconfig (archivo principal)

  [user]
    name = Tu Nombre
    email = <tunombre@gmail.com>
    # Este es el perfil por defecto si Git no encuentra un match en includeIf

[includeIf "gitdir:~/dev/github/personal/"]
  path = ~/.gitconfig-personal

[includeIf "gitdir:~/dev/gitlab/company/"]
  path = ~/.gitconfig-work

[core]
  editor = nano
  autocrlf = input

[color]
  ui = auto

[alias]
  st = status
  co = checkout
  ci = commit
  br = branch
  lg = log --oneline --graph --all

~/.gitconfig-personal

[user]
  name = Tu Nombre
  email = <tunombre@gmail.com>

📄 3. ~/.gitconfig-work

[user]
  name = Tu Nombre Profesional
  email = <tunombre@tuempresa.com>

✅ ¿Qué hace esta configuración?

    Cuando estés dentro de ~/dev/github/personal/**, Git usará el perfil personal.

    Cuando estés dentro de ~/dev/gitlab/company/**, Git usará el perfil profesional.

    En cualquier otro sitio, usará el perfil por defecto definido en [user] en ~/.gitconfig.
    
## Crea el entorno virtual y activa

  python3 -m venv venv
  source venv/bin/activate
  
## Paso 1: Instalar gh (si aún no lo tienes)

En macOS, con Homebrew:

  brew install gh

Luego autentícate:

  gh auth login

## Paso 2: Crear el repo desde tu proyecto local

En tu proyecto local:

  cd ~/mis-proyectos/mi-nuevo-repo
  git init
  git add .
  git commit -m "Primer commit"

Ahora crea el repositorio en GitHub con:

  gh repo create tu-usuario/mi-nuevo-repo --public --source=. --remote=origin (--push)

O, si prefieres privado:

  gh repo create tu-usuario/mi-nuevo-repo --private --source=. --remote=origin --push

Esto hace todo en un paso:

    Crea el repo en GitHub

    Lo enlaza como origin

    Hace git push

Crear rama de Git

  git checkout -b <branch>