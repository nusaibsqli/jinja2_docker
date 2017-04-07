# Jinja2 template rendering inside Dockerfile

Use this Docker image to render a template as follows:

You have a template file (e.g., `templates/test.json`)
```json
{
  "msg": "Hallo {{message}}"
}
```

You run the following command:
```bash
docker run --rm \
           -it \
           -v outputs:/out \
           -v templates:/data \
           -e TEMPLATE=test.json.j2 \
         	 -e OUT_FILE=/out/test.json \
           dominicbreuker/jinja_docker:latest message='welt'
```

This creates a file `outputs/test.json` with the following content:
```json
{
  "msg": "Hallo welt"
}
```
