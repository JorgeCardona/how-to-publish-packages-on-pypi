# HOW TO PUBLISH PACKAGES ON PYPI

# BASE STRUCTURE OF A PROJECT TO PUBLISH
# delete all folders that are not part of the project you created.
# delete the next yaml code to avoid errors with generating the binaries
```yaml
⭐ package_to_publish [project_directory]
┗ 🌼 src [package]
    ┗ 🦄 module_to_publish.py
    ┗ ❄️ __init__.py
┗ 🚀 test [package]
  ┗ test_module_to_publish.py
┗ ⛔.gitignore
┗ 🔑 LICENSE
┗ 🎁 README.md
┗ 🛒 requeriments.txt
┗ 🎯 setup.py
```

## Description of Project Files and Directories.

- **`src`**: This folder contains the source code that you want to publish. It is a common convention to have the Python package within this folder to avoid name conflicts. This folder includes the modules and code that will be distributed.

- **`README.md`**: A documentation file that describes your project. It should include details about the package's functionality, how to install it, usage examples, and any relevant information. This file is key, as PyPI will display it on the package page, making it the first thing users see.

- **`setup.py`**: The package configuration file. It contains metadata about the project such as name, version, description, dependencies, and other parameters. `setup.py` is used to generate the binaries (`sdist` and `bdist_wheel`) that will be published on PyPI. It also defines how the package and its dependencies are installed.

- **`test`**: A directory containing tests for the package. This is where files that verify that the code works correctly go. In this case, `test_module_to_publish.py` would be the file testing the functionalities of the module you want to publish.

- **`.gitignore`**: This file defines which files and directories should be ignored by Git. Typically, it includes files generated during compilation or execution (such as binaries or temporary files) to prevent them from being uploaded to the repository.

- **`LICENSE`**: A file that specifies the terms under which your code is available. It defines the rights and restrictions of using the package. This is important for the community so that users know under what license your software is distributed.

- **`requirements.txt`**: An optional file that lists the project dependencies, meaning the packages that need to be installed for the code to function correctly. It is useful for easily installing the dependencies in the development or production environment.

# STEPS CREATE PACKAGE DISTRIBUTION 

# Example - Repository for consultation
```bash
https://github.com/JorgeCardona/git-history-analyzer
```

### Install Dependencies
```bash
python -m pip install --upgrade setuptools wheel twine
```
![install_dependencies](https://raw.githubusercontent.com/JorgeCardona/how-to-publish-packages-on-pypi/refs/heads/main/images/install_dependencies.png)

### Generate Binaries
```bash
python setup.py sdist bdist_wheel
```
![generate_binaries](https://raw.githubusercontent.com/JorgeCardona/how-to-publish-packages-on-pypi/refs/heads/main/images/generate_binaries.png)

```yaml
⭐ package_to_publish [project_directory]
┗ 📦 build [package]
┗ 🌀 dist [package]
┗ 🌼 src [package]
    ┗ 🦄 module_to_publish.py
    ┗ ❄️ __init__.py
┗ 🚀 test [package]
  ┗ test_module_to_publish.py
┗ ⛔.gitignore
┗ 🔑 LICENSE
┗ 🎁 README.md
┗ 🛒 requeriments.txt
┗ 🎯 setup.py
```

- **`build` Directory**:
  - The `build` directory is where the output of the build process is stored. When you run the command to create the distribution package (e.g., `python setup.py sdist bdist_wheel`), the build process compiles your source code and prepares it for distribution. The `build` directory typically contains temporary files and artifacts generated during the build process. This directory can be safely deleted after the package is successfully created.

- **`dist` Directory**:
  - The `dist` directory is where the final distribution packages are stored after running the build command. This is the folder that contains the files you will upload to PyPI (Python Package Index) or Test PyPI. The contents of this directory usually include `.tar.gz` and `.whl` files, which are the source distribution and the wheel distribution of your package, respectively. These are the files that other users can install using pip.

### Install the created package on local machine/environment for testing the package
```bash
pip install -e .
```
![Install_package_on_local_machine](https://raw.githubusercontent.com/JorgeCardona/how-to-publish-packages-on-pypi/refs/heads/main/images/Install_package_on_local_machine.png)

### Publish on PyPI
## Generate API Token
![publish_pipy_api_token](https://raw.githubusercontent.com/JorgeCardona/how-to-publish-packages-on-pypi/refs/heads/main/images/publish_pipy_api_token.png)

### Publish on Test PyPI
## Create account in https://test.pypi.org/account/register/
```bash
twine upload --repository testpypi dist/* --verbose
```
![publish_pipy_test](https://raw.githubusercontent.com/JorgeCardona/how-to-publish-packages-on-pypi/refs/heads/main/images/publish_pipy_test.png)

### Publish Final Version on PyPI Prod
## Create account in https://pypi.org/account/register/
![publish_pipy_prod](https://raw.githubusercontent.com/JorgeCardona/how-to-publish-packages-on-pypi/refs/heads/main/images/publish_pipy_prod.png)

# Package Published on PYPI
![published_pypi_package](https://raw.githubusercontent.com/JorgeCardona/how-to-publish-packages-on-pypi/refs/heads/main/images/published_pypi_package.png)

# DOCUMENTACION EN ESPAÑOL
# Repositorio de referencia como ejemplo
```bash
https://github.com/JorgeCardona/git-history-analyzer
```

# CÓMO PUBLICAR PAQUETES EN PYPI

# ESTRUCTURA BÁSICA DE UN PROYECTO PARA PUBLICAR
# elimina todas las carpetas que no sean parte del proyecto que creaste.
# elimina el siguiente código yaml para evitar errores al generar los binarios
```yaml
⭐ package_to_publish [project_directory]
┗ 🌼 src [package]
    ┗ 🦄 module_to_publish.py
    ┗ ❄️ __init__.py
┗ 🚀 test [package]
  ┗ test_module_to_publish.py
┗ ⛔.gitignore
┗ 🔑 LICENSE
┗ 🎁 README.md
┗ 🛒 requeriments.txt
┗ 🎯 setup.py
```

## Descripción de Archivos y Directorios del Proyecto.

- **`src`**: Dentro de esta carpeta se encuentra el código fuente que deseas publicar. Es una convención común tener el paquete de Python dentro de esta carpeta para evitar conflictos de nombres. Esta carpeta contiene los módulos y el código que serán distribuidos.

- **`README.md`**: Archivo de documentación que describe tu proyecto. Debe incluir detalles sobre la funcionalidad del paquete, cómo instalarlo, ejemplos de uso, y cualquier información relevante. Este archivo es clave, ya que PyPI lo mostrará en la página del paquete y será lo primero que vean los usuarios.

- **`setup.py`**: Archivo de configuración del paquete. Contiene metadatos del proyecto como el nombre, versión, descripción, dependencias, y otros parámetros. `setup.py` se utiliza para generar los binarios (`sdist` y `bdist_wheel`) que serán publicados en PyPI. También define cómo se instala el paquete y sus dependencias.

- **`test`**: Directorio que contiene los tests o pruebas para el paquete. Aquí van los archivos que verifican que el código funcione correctamente. En este caso, `test_module_to_publish.py` sería el archivo que prueba las funcionalidades del módulo que deseas publicar.

- **`.gitignore`**: Este archivo define qué archivos y directorios deben ser ignorados por Git. Generalmente, se incluyen archivos generados durante la compilación o ejecución (como binarios o archivos temporales) para evitar que se suban al repositorio.

- **`LICENSE`**: Archivo que especifica los términos bajo los cuales tu código está disponible. Define los derechos y las restricciones de uso del paquete. Es importante para la comunidad y para que los usuarios sepan bajo qué licencia se distribuye tu software.

- **`requeriments.txt`**: Archivo opcional que lista las dependencias del proyecto, es decir, los paquetes que deben ser instalados para que el código funcione correctamente. Es útil para instalar fácilmente las dependencias del entorno de desarrollo o producción.


```python
import setuptools

with open("README.md", "r", encoding="utf-8") as file:
    long_description = file.read()

setuptools.setup(
    name="git-history-analyzer",
    version="0.0.8",
    author="Jorge Cardona",
    description="Generate Reports from Your Repository's Git History",
    long_description=long_description,
    long_description_content_type="text/markdown",
    url="https://github.com/jorgecardona/git-history-analyzer",
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: MIT License",
        "Operating System :: OS Independent",
    ],
    python_requires='>=3.6',
)
```

# PASOS PARA CREAR LA DISTRIBUCIÓN DEL PAQUETE

### Instalar dependencias
```bash
python -m pip install --upgrade setuptools wheel twine
```
![install_dependencies](https://raw.githubusercontent.com/JorgeCardona/how-to-publish-packages-on-pypi/refs/heads/main/images/install_dependencies.png)


### Generar binarios
```bash
python setup.py sdist bdist_wheel
```
![generate_binaries](https://raw.githubusercontent.com/JorgeCardona/how-to-publish-packages-on-pypi/refs/heads/main/images/generate_binaries.png)

```yaml
⭐ package_to_publish [project_directory]
┗ 📦 build [package]
┗ 🌀 dist [package]
┗ 🌼 src [package]
    ┗ 🦄 module_to_publish.py
    ┗ ❄️ __init__.py
┗ 🚀 test [package]
  ┗ test_module_to_publish.py
┗ ⛔.gitignore
┗ 🔑 LICENSE
┗ 🎁 README.md
┗ 🛒 requeriments.txt
┗ 🎯 setup.py
```
- **Directorio `build`**:
  - El directorio `build` es donde se almacenan los resultados del proceso de construcción. Cuando ejecutas el comando para crear el paquete de distribución (por ejemplo, `python setup.py sdist bdist_wheel`), el proceso de construcción compila tu código fuente y lo prepara para su distribución. Este directorio suele contener archivos temporales y artefactos generados durante el proceso de construcción. Este directorio se puede eliminar de forma segura después de que el paquete se haya creado con éxito.

- **Directorio `dist`**:
  - El directorio `dist` es donde se almacenan los paquetes de distribución finales después de ejecutar el comando de construcción. Esta es la carpeta que contiene los archivos que subirás a PyPI (Python Package Index) o a Test PyPI. El contenido de este directorio generalmente incluye archivos `.tar.gz` y `.whl`, que son la distribución de código fuente y la distribución de ruedas de tu paquete, respectivamente. Estos son los archivos que otros usuarios pueden instalar usando pip.
  
### Instalar el paquete creado en la máquina local/entorno para probar el paquete
```bash
pip install -e .
```
![Install_package_on_local_machine](https://raw.githubusercontent.com/JorgeCardona/how-to-publish-packages-on-pypi/refs/heads/main/images/Install_package_on_local_machine.png)


### Publicar el paquete en PyPI
## Generar el API Token
![publish_pipy_api_token](https://raw.githubusercontent.com/JorgeCardona/how-to-publish-packages-on-pypi/refs/heads/main/images/publish_pipy_api_token.png)


### Publicar el paquete en Test PyPI
## Create account in https://test.pypi.org/account/register/
```bash
twine upload --repository testpypi dist/* --verbose
```

![publish_pipy_test](https://raw.githubusercontent.com/JorgeCardona/how-to-publish-packages-on-pypi/refs/heads/main/images/publish_pipy_test.png)

### Publicar la version final del paquete en Prod PyPI
## Create account in https://pypi.org/account/register/

![publish_pipy_prod](https://raw.githubusercontent.com/JorgeCardona/how-to-publish-packages-on-pypi/refs/heads/main/images/publish_pipy_prod.png)

# Paquete publicado en PYPI
![published_pypi_package](https://raw.githubusercontent.com/JorgeCardona/how-to-publish-packages-on-pypi/refs/heads/main/images/published_pypi_package.png)

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact
Project Link: [GitHub Repository](https://github.com/jorgecardona/how-to-publish-packages-on-pypi)