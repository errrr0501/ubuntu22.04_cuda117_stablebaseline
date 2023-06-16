# Steps for usage
<!-- TODO: change to asciidoc -->
<!-- BUG: container name = image -->
## English version

1. Install Docker Engine.
    - [Docker Engine](https://docs.docker.com/engine/install/)
    - [linux post-installation](https://docs.docker.com/engine/install/linux-postinstall/)

2. Download this github repository.

    ```shell
    git clone https://github.com/errrr0501/docker_20.04_cuda12_tf1.15
    ```

3. Copy to your project directory.
    - `<workspace_path>`: replace with real project folder path.

        ```shell
        cp -r docker_template <workspace_path>
        # or
        cp -r docker_template <workspace_path>/docker
        ```

    - Example:

        ```shell
        # ROS format workspace
        cp -r docker_template ~/test_ws/src
        ```

4. Adjust Dockerfile to suit your needs
5. Build Docker image (run `build.sh`).
    - `<docker_path>` replace with real to docker location.

    ```shell
    ./<docker_path>/build.sh
    ```

6. Run Docker container (run `run.sh`).
    - `<docker_path>` replace with real to docker location.

    ```shell
    ./<docker_path>/run.sh
    ```

7. Enjoy Docker support.

### Pay attention to the following points when using

1. Docker image name wil be named based on the follwing order:
    - Dockerfile name (suffix), ex: **Dockerfile_DuckDuckGo**, the image name will be **DuckDuckGo**.
    - Workspace folder name (prefix), ex: **Microsoft_ws**, the image name will be **Microsoft**.
    - If neither exists, the image name will be **unknown**.

2. Docker container name will be named in the format of `<user>/<container>` and named based on the following order:
    - `<user>`:
        - Docker login username.
        - system username.
        - if neither exists, `<user>` will be named initial.
    - `<container>`:
        - Workspace folder name (prefix), ex: **chrome_ws**, the container name will be **chrome**.
        - Dockerfile name (suffix), ex: **Dockerfile_Firefox**, the container name will be **Firefox**.
        - If neither exists, the container name will be **unknown**.


3. Dockerfile and entrypoint.sh notes:
    - It is possible to add hardware architecture as a suffix to the file name.
       - ex: **Dockerfile_x86_64** or **Dockerfile_aarch64**.
       - ex: **entrypoint_x86_64.sh** or **entrypoint_aarch64.sh**.
    - If there are multiple Dockerfile or entrypoint.sh file in the docker folder, the script will use the one that matches the current hardware architecture.
