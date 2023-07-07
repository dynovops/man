# Instalación de Docker en Ubuntu

1. Eliminar paquetes que pueden generar conflicto
    ```
    for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
    ```

2. Instalar de paquetes básicos para el uso del repositorio de Docker
    ```
    sudo apt-get update
    ```
    ```
    sudo apt-get install ca-certificates curl gnupg
    ```

3. Instalar la llave GPG de Docker
    ```
    sudo install -m 0755 -d /etc/apt/keyrings
    ```
    ```
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    ```
    ```
    sudo chmod a+r /etc/apt/keyrings/docker.gpg
    ```

4. Instalar repositorio oficial de Docker
    ```
    echo \
    "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
    sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    ```

5. Instalar Docker
    ```
    sudo apt-get update
    ```
    ```
    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    ```

6. Probar isnatalación
    ```
    sudo docker run hello-world
    ```
