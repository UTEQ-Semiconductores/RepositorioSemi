Liga:[[Estrategia Repositorio]]
# Configuración de Infraestructura Base para Repositorio Educativo en Ingeniería de Semiconductores

## 1. Crear repositorio en GitHub

1. **Crear una cuenta en GitHub** (si aún no tienes una)
    
2. **Crear un nuevo repositorio**:
    
    - Nombre sugerido: `semiconductores-repo` o `ingenieria-semiconductores`
    - Descripción: "Repositorio educativo integral para ingeniería en semiconductores"
    - Visibilidad: Pública (recomendado para material educativo)
    - Inicializar con README.md
    - Añadir licencia: Creative Commons (CC-BY o CC-BY-SA)
3. **Configurar GitHub Pages**:
    
    - Ir a Settings > Pages
    - Source: Branch "main" (o "master")
    - Folder: "/" (root) o "/docs" (según prefieras organizar)

## 2. Configuración local

1. **Instalar requisitos previos**:
    
    ```bash
    # Instalar Ruby (necesario para Jekyll)
    # En Ubuntu/Debian:
    sudo apt-get install ruby-full build-essential zlib1g-dev
    
    # En macOS (con Homebrew):
    brew install ruby
    
    # En Windows:
    # Descargar e instalar Ruby con DevKit desde https://rubyinstaller.org/
    
    # Instalar Bundler y Jekyll
    gem install bundler jekyll
    ```
    
2. **Clonar el repositorio**:
    
    ```bash
    git clone https://github.com/tu-usuario/semiconductores-repo.git
    cd semiconductores-repo
    ```
    

## 3. Configurar Jekyll

1. **Inicializar Jekyll**:
    
    ```bash
    # Opción 1: Crear nuevo sitio Jekyll
    jekyll new . --force
    
    # Opción 2: Si prefieres usar un tema educativo específico como Just the Docs
    # (recomendado para repositorios educativos)
    gem install bundler jekyll
    mkdir docs
    cd docs
    jekyll new . --blank
    ```
    
2. **Editar el archivo `_config.yml`**:
    
    ```yaml
    # Información del sitio
    title: Repositorio de Ingeniería en Semiconductores
    description: >- 
      Repositorio educativo integral para la licenciatura 
      en ingeniería en semiconductores
    baseurl: "/semiconductores-repo" # el nombre de tu repositorio
    url: "https://tu-usuario.github.io" # tu dominio de GitHub Pages
    
    # Configuración de tema (por ejemplo, Just the Docs)
    remote_theme: pmarsceill/just-the-docs
    # O tema instalado localmente
    # theme: minima
    
    # Configuración de navegación y estructura
    collections:
      fundamentos:
        output: true
        permalink: /:collection/:path/
      electronica:
        output: true
        permalink: /:collection/:path/
      fabricacion:
        output: true
        permalink: /:collection/:path/
      diseno_circuitos:
        output: true
        permalink: /:collection/:path/
      instrumentacion:
        output: true
        permalink: /:collection/:path/
      programacion:
        output: true
        permalink: /:collection/:path/
    
    # Configuración de compilación
    markdown: kramdown
    highlighter: rouge
    
    kramdown:
      math_engine: mathjax
      syntax_highlighter: rouge
    
    # Plugins útiles
    plugins:
      - jekyll-feed
      - jekyll-seo-tag
      - jekyll-sitemap
      - jekyll-relative-links
      - jekyll-optional-front-matter
    ```
    
3. **Crear estructura básica de directorios**:
    
    ```bash
    # Crear directorios principales según las áreas temáticas
    mkdir -p _fundamentos _electronica _fabricacion _diseno_circuitos _instrumentacion _programacion
    
    # Crear directorios para recursos comunes
    mkdir -p assets/images assets/css assets/js _layouts _includes _data
    ```
    
4. **Crear Gemfile**:
    
    ```ruby
    source "https://rubygems.org"
    
    gem "jekyll", "~> 4.2.0"
    gem "webrick", "~> 1.7"
    
    # Temas - descomenta el que prefieras usar
    # gem "minima", "~> 2.5"
    gem "just-the-docs"
    
    # Plugins
    group :jekyll_plugins do
      gem "jekyll-feed", "~> 0.12"
      gem "jekyll-seo-tag"
      gem "jekyll-sitemap"
      gem "jekyll-relative-links"
      gem "jekyll-optional-front-matter"
    end
    
    # Windows e ingeniería específica
    platforms :mingw, :x64_mingw, :mswin, :jruby do
      gem "tzinfo", "~> 1.2"
      gem "tzinfo-data"
    end
    ```
    
5. **Probar localmente**:
    
    ```bash
    bundle install
    bundle exec jekyll serve
    ```
    
6. **Verificar el sitio** en http://localhost:4000/
    

## 4. Realizar primer commit y push

1. **Añadir archivos al control de versiones**:
    
    ```bash
    git add .git commit -m "Configuración inicial de Jekyll para repositorio educativo"git push origin main
    ```
    

## 5. Verificar despliegue en GitHub Pages

1. Esperar unos minutos después del push
2. Visitar `https://tu-usuario.github.io/semiconductores-repo`
3. Verificar que el sitio se ha desplegado correctamente