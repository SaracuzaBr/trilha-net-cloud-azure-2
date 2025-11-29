# Desafio de Consolidação: Provisionamento de Banco de Dados (PaaS) no Azure

Este projeto é um repositório de documentação e anotações técnicas que detalha o processo de configuração de um serviço de Banco de Dados na plataforma Microsoft Azure, conforme a Trilha de Aprendizagem [Nome da Sua Trilha/Bootcamp].

O objetivo principal é transformar a execução prática (configuração do Azure Database) em material didático e estruturado para referência futura.

---

## 🛠️ O Contexto: PaaS e o Banco de Dados como Serviço

A criação de um Banco de Dados no Azure (como Azure SQL Database ou Azure Database for MySQL/PostgreSQL) é o exemplo clássico de **PaaS (Plataforma como Serviço)**.

| Característica | Detalhe | Benefício para o Desenvolvedor |
| :--- | :--- | :--- |
| **Foco** | SQL Database / Dados | Concentra-se apenas na estrutura do banco, tabelas e consultas. |
| **Gerenciamento** | A Azure gerencia o sistema operativo, a rede, o armazenamento, as atualizações de software e o *backup*. | Não há preocupação com a manutenção da infraestrutura ou com a gestão do SO. |
| **Modelo** | PaaS | Maior agilidade e menor responsabilidade de gerenciamento. |

---

## 📝 Documentação do Processo: Criação da Instância de Banco de Dados

Abaixo estão os passos cruciais e as decisões tomadas durante o provisionamento de uma instância de banco de dados no Azure.

### 1. Pré-Requisitos e Setup Inicial

| Ação | Configuração Realizada | Conceito Relacionado |
| :--- | :--- | :--- |
| **Grupo de Recursos** | `rg-db-desafio` (Nome Sugerido) | **Gerenciabilidade**: Agrupa todos os serviços relacionados (servidor, base de dados, regras de firewall) para facilitar a administração e o custo operacional (OpEx). |
| **Serviço Selecionado** | Azure SQL Database (ou similar) | **PaaS**: A Microsoft fornece a plataforma de banco de dados pronta a usar. |

### 2. Configuração do Servidor e Credenciais

| Configuração | Descrição da Escolha | Importância |
| :--- | :--- | :--- |
| **Nome do Servidor** | Nome Único Global (Ex: `srv-db-desafio-unique`) | Endereço único para acesso via aplicações externas (Ex: uma aplicação Node.js ou .NET). |
| **Credenciais** | Login e Senha de Administrador | Acesso de nível mais alto para gestão e administração do banco. |
| **Localização** | Escolhida a região mais próxima (Ex: *East US / Brazil South*) | Otimiza a latência para os utilizadores da aplicação. |

### 3. Camada de Serviço e Custos

* **Objetivo:** Definir o nível de performance e o custo OpEx (pago por consumo).
* **Decisão:** A camada de serviço (Ex: *Basic, Standard, Premium* ou V-Cores) foi selecionada com base no orçamento e nos requisitos de desempenho da aplicação.

### 4. Configuração de Rede e Segurança (Firewall)

Esta é a etapa mais crítica para o acesso e a segurança.

| Configuração | Ação Realizada | Justificativa de Segurança |
| :--- | :--- | :--- |
| **Regras de Firewall** | Adição do **Endereço IP público** do desenvolvedor. | Restringe o acesso ao servidor de banco de dados a IPs conhecidos (medida essencial de **segurança de rede**). |
| **Serviços Azure** | Desabilitado (ou Revisado) | Impede que todos os outros serviços Azure acessem este banco de dados por padrão, a menos que explicitamente permitido. |
| **Conectividade** | Definição de **Ponto de Extremidade Privado** (se aplicável a nível avançado) | Garante que o tráfego do banco de dados permaneça na rede interna da Azure (melhorando a segurança e o desempenho). |

---

## 💡 Dicas de Implementação e Documentação

* **OpEx vs. CapEx:** Lembre-se de que, ao usar o Azure SQL Database, estás a investir em OpEx, pagando pelo uso do serviço, em contraste com o CapEx (compra e manutenção de servidores SQL Server físicos).
* **Documentação Contínua:** Mantenha a documentação atualizada no seu `README.md` sempre que adicionar uma nova *feature* ou regra de segurança ao banco de dados.
* **Capturas de Tela:** Se optares por usar a pasta `/images`, inclua capturas da tela de **Configurações de Rede** (Regras de Firewall) e da **Página de Visão Geral** (Overview) do servidor.

---

## 🔗 Próximos Passos (Git/GitHub)

Para concluir a entrega do projeto:

1.  Cria o arquivo `.gitignore` (comando: `dotnet new gitignore` se estiver numa pasta .NET, ou obtém o modelo para Node/Geral).
2.  Inicializa o Git no teu projeto:
    ```bash
    git init
    git add .
    git commit -m "docs: Estrutura inicial e documentacao do PaaS Azure SQL"
    ```
3.  Conecta ao repositório do GitHub e envia o código:
    ```bash
    git remote add origin [https://www.youtube.com/watch?v=BW1w0P1KNk0](https://www.youtube.com/watch?v=BW1w0P1KNk0)
    git push -u origin main
    ```
