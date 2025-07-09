# Deploy do Projeto Calhas Gaspar

## Configuração para GitHub Pages

Este projeto está configurado para deploy automático no GitHub Pages com domínio personalizado `calhasgaspar.com`.

### Pré-requisitos

1. Ter o projeto no GitHub
2. Configurar o domínio personalizado no GitHub Pages
3. Configurar DNS do domínio

### Configurações Realizadas

1. **vite.config.js**: Configurado base path para produção
2. **package.json**: Adicionados scripts de deploy
3. **GitHub Actions**: Workflow automático de deploy
4. **CNAME**: Arquivo para domínio personalizado

### Como Fazer o Deploy

#### Opção 1: Deploy Automático (Recomendado)
- Faça push para a branch `main`
- O GitHub Actions irá automaticamente fazer o build e deploy

#### Opção 2: Deploy Manual
```bash
npm run deploy
```

### Configuração do Domínio

1. No repositório do GitHub, vá em Settings > Pages
2. Configure o domínio personalizado como `calhasgaspar.com`
3. Configure o DNS do domínio:
   - Tipo: CNAME
   - Nome: @
   - Valor: `seu-usuario.github.io`

### Estrutura de Branches

- `main`: Branch principal com o código fonte
- `gh-pages`: Branch criada automaticamente pelo GitHub Actions com os arquivos de produção

### Verificação

Após o deploy, o site estará disponível em:
- https://calhasgaspar.com
- https://seu-usuario.github.io/calhas-gaspar (fallback) 