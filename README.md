<h1 align="center">Onedefine</h1>

Onedefine is a tool for define your isolator variable in only one file.

Getting Started
---

- You need to create an executeable file with your custom variable in it then ended by `curl` statement.

    - `name` : As your image name.
    - `version` : As your image version.
    - `ignore` : As replacement for your .dockerignore.
    - `build` : As replacement for your Dockerfile.

    Sample file :

    ```sh
    name='collection'
    version='1.0.0'

    ignore=$(cat <<EOF

    .git*
    .gitignore
    Dockerfile*
    docker-compose*
    README.md

    EOF
    )

    build=$(cat <<EOF

        FROM alpine:3.12

        WORKDIR /var/www/$name/
        COPY . .

        ENTRYPOINT []
        CMD ['tail', '-f', '/dev/null']

    EOF
    )

    curl -sL https://raw.githubusercontent.com/hsbmaulana/onedefine/1.0.0/bin/run | . /dev/stdin
    ```

Usage
---

`sh yourexecuteablefile <option>`

Option
---

- `help` : Usage.
- `build` : Build you image file as your defined variable.
- `remove` : Remove you image file as your defined variable.
- `status` : List your status image.
- `clean` : Clean all unused dependencies container and image.

Author
---

- Hasby Maulana ([@hsbmaulana](https://linkedin.com/in/hsbmaulana))
