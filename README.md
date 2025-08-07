Dominando Armazenamento na Azure com AzCopy
 Objetivo do Projeto
Demonstrar na prática:

Criação de uma conta de armazenamento

Configuração de containers

Ativação de backup

Migração de arquivos via AzCopy

Geração e uso de tokens SAS para segurança

🚀 Etapas do Projeto
1️⃣ Criar Conta de Armazenamento
Acesse o Portal Azure

Vá em "Contas de Armazenamento"

Clique em "Criar"

Preencha os campos:

Nome: armazenamentohumberto

Tipo: StorageV2 (uso geral v2)

Replicação: Locally-redundant storage (LRS)

Região: sua região mais próxima

Clique em "Revisar + Criar"

2️⃣ Criar Containers
Acesse sua conta de armazenamento

Vá em "Contêineres" > "Novo Contêiner"

Nome: azcopy-container

Nível de acesso público: privado (recomendado)

Clique em "Criar"

3️⃣ Ativar Backup (opcional)
No menu lateral da conta, vá em Backup center

Configure políticas de backup para blobs

Escolha: ponto de recuperação, retenção, política de agendamento

4️⃣ Instalar e Configurar o AzCopy
AzCopy é uma ferramenta de linha de comando para transferências de dados entre seu computador e a Azure.

Baixe: Download AzCopy

Extraia o executável em uma pasta do seu sistema

Adicione o caminho do azcopy.exe às variáveis de ambiente (opcional)

5️⃣ Gerar Token SAS (Shared Access Signature)
Na conta de armazenamento > vá em Contêineres > selecione azcopy-container

Clique em “Gerar SAS”

Selecione:

Permissões: rwl (Leitura, Escrita, Listagem)

Protocolo: HTTPS

Defina o intervalo de tempo de validade

Clique em “Gerar Token e URL”

Copie o link com SAS ou apenas o token para uso posterior

6️⃣ Usar AzCopy com Token
Exemplo de comando para upload de um arquivo:

bash
Copiar
Editar
azcopy copy "C:\meus-arquivos\relatorio.xlsx" "https://armazenamentohumberto.blob.core.windows.net/azcopy-container?sv=2025-08-07&ss=b&srt=sco&sp=rwl&se=2025-08-08T23:59Z&st=2025-08-07T00:00Z&spr=https&sig=abc123..." --recursive=true
Para download de arquivos:

bash
Copiar
Editar
azcopy copy "https://armazenamentohumberto.blob.core.windows.net/azcopy-container/relatorio.xlsx?..." "C:\meus-arquivos\" --recursive=true
🔐 Segurança
Tokens SAS devem ter validade curta e permissões mínimas

