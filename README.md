# Liferay

## Setup com Docker Compose Local

Execute o setup inicial do workspace:


### Crie as pastas:

```
mkdir -p bundles/deploy
mkdir -p bundles/logs
mkdir -p bundles/osgi/client-extensions
mkdir -p bundles/osgi/modules
mkdir -p bundles/osgi/war
```

### Ajustar permissões:

```
chmod -R 777 bundles
chmod -R 777 docker-compose/elasticsearch-data
chmod -R 777 docker-compose/liferay-document-library
```

### Restaurar Backup (Opcional)

Copie o DUMP do banco para a basta mysql-dump:

```
cp database-dump.sql ${YOUR_WORKSPACE_PATH}/docker-compose/mysql-dump/
```

Copie a Document Library para a pasta correspondente mapeada para o serviço Liferay:

```
cp -R document-library/* ${YOUR_WORKSPACE_PATH}/docker-compose/liferay-document-library/
```

### Executar o ambiente:

Execute o comando abaixo para subir o ambiente:

```
docker compose up --build -d
```

Para ver os logs:

```
docker compose logs -f liferay
```

### Deploy dos temas

Após subir, faça o deploy dos temas, para que o ambiente fique exatamente igual:

```
cd themes/
blade gw deploy
```
