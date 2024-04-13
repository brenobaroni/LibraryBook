Configurando o Google Storage para aceitar cross-origin="anonymous" pelo terminal
Para configurar o Google Storage para aceitar cross-origin="anonymous" pelo terminal, siga estas etapas:

1. Instale a gcloud CLI:

Se você ainda não instalou a gcloud CLI, siga as instruções em https://cloud.google.com/sdk/docs/install.
2. Acesse o seu projeto do Google Cloud Platform:

Execute o seguinte comando no terminal:
gcloud auth login
Siga as instruções na tela para fazer login em sua conta do Google Cloud Platform.
Selecione o projeto do Google Cloud Platform que contém o bucket que você deseja configurar.
3. Crie um arquivo JSON de configuração CORS:

Crie um arquivo JSON com a seguinte configuração:
JSON
{
  "cors": [
    {
      "origin": "*",
      "method": [
        "GET",
        "PUT",
        "POST",
        "DELETE",
        "HEAD"
      ],
      "requestHeaders": [
        "Origin",
        "Content-Type",
        "Authorization"
      ],
      "responseHeaders": [
        "Access-Control-Allow-Origin",
        "Access-Control-Allow-Methods",
        "Access-Control-Allow-Headers"
      ]
    }
  ]
}
Use o código com cuidado.
Salve o arquivo JSON como cors.json.
4. Aplique a configuração CORS ao seu bucket:

Execute o seguinte comando no terminal, substituindo your-bucket-name pelo nome do seu bucket:
gsutil cors set cors.json gs://your-bucket-name
5. Teste a configuração CORS:

Abra uma nova guia do navegador da web.
Acesse o URL do seu bucket, como https://storage.googleapis.com/your-bucket-name/your-file-name.
Verifique o console do navegador para ver se há erros de CORS.
Observações:

Se você precisar permitir acesso de origens específicas, poderá modificar o arquivo cors.json para incluir origens específicas.
Você também pode usar a API gsutil XML para configurar regras CORS.
Recursos adicionais:

Documentação do Google Cloud Storage sobre CORS: https://cloud.google.com/storage/docs/using-cors
Exemplo de configuração de CORS para o Cloud Storage: https://cloud.google.com/storage/docs/using-cors
