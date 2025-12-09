# Estratégia de Gestão de Identidade e Acesso (IAM)

## 1. Princípio do Menor Privilégio (PoLP)
O FoundLab Umbrella requer papéis IAM mínimos para operar:
* `roles/run.invoker`: Para aceitar tráfego.
* `roles/cloudkms.cryptoKeyEncrypterDecrypter`: Para empacotar/desempacotar DEKs.
* `roles/logging.logWriter`: Para enviar logs de auditoria.

## 2. Sem Chaves de Conta de Serviço (Service Account Keys)
**Política Estrita:** Nós não geramos, baixamos ou armazenamos chaves JSON de Service Accounts.
* **Autenticação:** Todos os serviços usam **Workload Identity** para autenticar nas APIs do Google.
* **Federação:** Pipelines de CI/CD autenticam via Federação OIDC.

## 3. Procedimentos de Emergência (Break-Glass)
Como a infraestrutura é hospedada pelo consumidor, a FoundLab **NÃO** possui acesso remoto (SSH/RDP) aos containers de produção. A solução de problemas depende inteiramente de métricas e logs estruturados exportados para as ferramentas do cliente.