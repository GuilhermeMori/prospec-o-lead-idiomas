# Workflow n8n — Captura de Leads Multilíngue

Workflow para n8n que captura leads vindos de formulários web e dispara mensagens automáticas de acordo com o idioma selecionado pelo lead.

## Fluxo

1. Um webhook recebe os dados do formulário (nome, email, telefone, cidade, idioma, etc.)
2. Os parâmetros UTM são extraídos da URL da página de origem
3. Uma mensagem de boas-vindas é gerada no idioma do lead (inglês, espanhol, francês, alemão ou italiano)
4. O telefone é limpo e formatado com DDI baseado no idioma
5. Uma conversa é criada via API da plataforma de atendimento
6. O contato recebe um marcador (tag) com o mês atual
7. O lead é adicionado ao CRM com dados de UTM e descrição

## Idiomas suportados

| Idioma    | DDI padrão |
|-----------|------------|
| Inglês    | +44        |
| Espanhol  | +595       |
| Francês   | +33        |
| Alemão    | +49        |
| Italiano  | (default +55) |

## Configuração

Antes de importar, substitua os placeholders no JSON:

| Placeholder            | Descrição                              |
|------------------------|----------------------------------------|
| `SEU_DOMINIO.com`      | Domínio da sua plataforma de atendimento |
| `SEU_TOKEN_AQUI`       | Token de acesso da API                 |
| `SEU_CRM_TOKEN_AQUI`   | Token de acesso do CRM                 |
| `SEU_WEBHOOK_PATH_AQUI`| Path do webhook no n8n                 |
| `SEU_WEBHOOK_ID_AQUI`  | ID do webhook no n8n                   |
| `SEU_INBOX_ID`         | ID da inbox na plataforma              |

## Como usar

1. Importe o arquivo `capturar-lead.json` no n8n
2. Substitua todos os placeholders listados acima
3. Configure o webhook no seu formulário para apontar para a URL gerada pelo n8n
4. Ative o workflow
