<p align="center">
<img src="https://cwmkt.com.br/wp-content/uploads/2024/04/logo_github.png" width="240" />
<p align="center">Seja bem-vindo ao Guia de Instalação EasyPanel Langfuse 🚀</p>
</p>
  
<p align="center"> 
<a href="https://hubconnect.top" target="_blank">👉 Participe da Comunidade HubConnect 👈</a>
</p>

<hr />
<hr />

## Comando para Instalar EasyPanel

```bash
curl -sSL https://get.easypanel.io | sh
```

Adicione nome de Project

![48098522-0c485df00f5cadb0d329061c35fee46c](https://github.com/cwmkt/easypanelevotypebot/assets/91642837/b72c1359-91ca-4bf6-9fb1-32525ba5747b)

Clique na aba Templates

![48098535-90f9b4f370bb8b06cfd7e4acf0ee0f97](https://github.com/cwmkt/easypanelevotypebot/assets/91642837/03c1830c-621c-40b3-94ee-93eb568c8d2e)

Va ate final da pagina

![image](https://github.com/comunidadehubconnect/easypanelwoofedcrm/assets/91642837/828a9e88-45f2-4b6b-98f1-ab4f164d2889)

Adicione codigo abaixo dentro do Schema

![image](https://github.com/comunidadehubconnect/easypanelwoofedcrm/assets/91642837/74b97f33-e5d2-495d-aaba-25bb8b433adf)

```bash
{
  "services": [
    {
      "type": "app",
      "data": {
        "projectName": "langfuse",
        "serviceName": "langfuse-server",
        "source": {
          "type": "image",
          "image": "langfuse/langfuse:2"
        },
        "domains": [
          {
            "host": "$(EASYPANEL_DOMAIN)",
            "port": 3000
          }
        ],
      "env": "DATABASE_URL=postgresql://postgres:postgres@db:5432/postgres \nNEXTAUTH_SECRET=mysecret \nSALT=mysalt \nNEXTAUTH_URL=https://$(EASYPANEL_DOMAIN)"
      }
    },
    {
      "type": "app",
      "data": {
        "projectName": "db",
        "serviceName": "db-langfuse",
        "source": {
          "type": "image",
          "image": "postgres"
        },
        "domains": [
          {
            "host": "$(EASYPANEL_DOMAIN)",
            "port": 5432
          }
        ],
        "env":"POSTGRES_USER=postgres \nPOSTGRES_PASSWORD=postgres \nPOSTGRES_DB=postgres",
        "mounts": [
          {
            "type": "volume",
            "name": "database_data",
            "mountPath": "/var/lib/postgresql/data"
          }
        ]
      }
    }
  ]
}
```


Pronto tudo Funcionando ✅😎

Creditos: Andre Marques
