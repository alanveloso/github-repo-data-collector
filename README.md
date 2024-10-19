# github-repo-data-collector

Este projeto consiste em dois scripts Python:

1. **coletor_github.py**: Monitora o número de commits e releases em repositórios do GitHub, permitindo analisar a atividade de desenvolvimento.
2. **repository_age_calculator.py**: Calcula o tempo de existência de repositórios do GitHub em meses, desde a data de criação até um mês e ano fornecidos. O objetivo é permitir a comparação da maturidade entre diferentes projetos ao longo do tempo. Os resultados são salvos em arquivos CSV.

## Funcionalidades

### Monitoramento de Commits e Releases

- Coleta informações sobre o número de commits e releases em repositórios do GitHub.
- Permite que o usuário especifique um mês e um ano para consultar as atividades desses repositórios.
- Salva os dados em um arquivo CSV com o nome do repositório, o número de commits e o número de releases.

### Cálculo da Idade dos Repositórios

- Calcula a idade dos repositórios em meses, a partir da data de criação até um mês e ano finais específicos.
- Verifica se a data fornecida é anterior à criação do repositório e exibe uma mensagem de erro apropriada.
- Salva os resultados em um arquivo CSV com o nome do repositório, a data de criação e a idade em meses.

## Como Usar

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/github-repo-data-collector.git

2. Instale as dependências necessárias:
  ```bash
   pip install requests
```

3. Substitua o token do GitHub nos scripts: No arquivo **coletor_github.py** e no arquivo **repository_age_calculator.py**, substitua o valor da variável ```token``` pelo seu token pessoal do GitHub, que é necessário para acessar a API do GitHub.

4. Execute o script de monitoramento:
  ```bash
python coletor_github.py
```
*Durante a execução, você será solicitado a inserir o mês (MM) e o ano (YYYY) para consultar.*

5. Execute o script de cálculo da idade:
  ```bash
python repository_age_calculator.py
```
*Durante a execução, você será solicitado a inserir o ano final (YYYY) e o mês final (MM) para calcular a idade dos repositórios.*

### Configurando o Token do GitHub

Para que os scripts funcionem corretamente, você precisará fornecer um token pessoal do GitHub. Esse token deve ter permissões de leitura para repositórios públicos (e, se necessário, privados). Veja os passos para gerar o token:

1. Vá até as configurações de tokens pessoais do GitHub.
2. Clique em "Generate new token" e selecione as permissões necessárias.
4. Copie o token e cole no lugar da variável ```token``` nos scripts.

### Exemplo de Saída
Após a execução dos scripts, os seguintes arquivos CSV serão gerados:

1. dados_commits_releases.csv:
  ```bash
Repositório,Commits,Releases
hyperledger-labs/fablo,1547,9
hyperledger-labs/fabric-operator,99,18
hyperledger-labs/ansible-collection,116,1
...
```

2. repositorios_com_idade.csv:
  ```bash
Repositório,Data de Criação,Idade em Meses
hyperledger-labs/fablo,2019-11-29T11:01:59Z,59
hyperledger-labs/fabric-operator,2022-06-07T18:16:42Z,28
hyperledger-labs/ansible-collection,2023-02-21T16:43:19Z,20
...
```

## Observações
- Se a data final fornecida for anterior à criação do repositório, o script exibirá uma mensagem de erro.
- Repositórios com menos de um mês serão registrados como "0" no campo "Idade em Meses".
