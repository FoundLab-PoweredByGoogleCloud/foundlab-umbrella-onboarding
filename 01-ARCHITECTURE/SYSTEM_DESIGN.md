# Design do Sistema: O Padrão "Enclave Cavalo de Troia"

## 1. Filosofia Arquitetural
O FoundLab Umbrella utiliza uma arquitetura **Single-Tenant, Hospedada no Consumidor**. Ao contrário do SaaS multi-tenant tradicional, nosso software roda inteiramente na infraestrutura do cliente.

### 1.1 A Promessa de "Zero Persistência"
* **Ingestão:** Dados entram via canais criptografados mTLS 1.3.
* **Processamento:** Ocorre estritamente em memória volátil (RAM). O SWAP é desabilitado no nível do kernel.
* **Terminação:** Ao completar a requisição, a memória é liberada. Nenhum dado é gravado em armazenamento persistente (Disco/DB) dentro do enclave.

## 2. Isolamento Computacional (gVisor)
Todos os containers de carga de trabalho são implantados no **Cloud Run (Gen2)** com o ambiente de execução **gVisor** habilitado.
* **Defesa:** O gVisor fornece uma camada distinta de isolamento de kernel, prevenindo ataques de "container escape" e mitigando vulnerabilidades de syscall.

## 3. Isolamento de Rede
* **Entrada (Ingress):** Apenas via Private Service Connect (PSC). Nenhum IP Público é atribuído aos nós de computação.
* **Saída (Egress):** Restrita via VPC Service Controls. O tráfego de saída é bloqueado por padrão, com liberação estrita apenas para APIs do Google (KMS, Logging).