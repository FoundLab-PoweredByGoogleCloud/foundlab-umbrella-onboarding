# FoundLab Umbrella - Kit de Defesa de Segurança e Compliance

**Classificação:** CONFIDENCIAL
**Público-Alvo:** Auditoria de Segurança Google Cloud (L8+) e Gestão de Risco Financeiro.
**Escopo de Compliance:** ISO 27001:2022, Preparação SOC 2 Tipo II, LGPD/GDPR.

## 🛡️ Resumo Executivo
O FoundLab Umbrella opera sob um modelo de **Estrita Zero-Persistência** dentro de um enclave hospedado no cliente (Consumer-Hosted). Esta arquitetura move a fronteira de confiança inteiramente para a VPC do cliente, garantindo que a FoundLab (o fornecedor) tenha **zero acesso** a PII ou MNPI (Informação Material Não Pública).

## 🔑 Pilares de Segurança
1.  **Soberania:** Os dados nunca deixam o perímetro de Controles de Serviço da VPC (VPC-SC) do cliente.
2.  **Processamento Efêmero:** Instâncias Cloud Run operam sem estado (apenas RAM). Sem discos montados.
3.  **Auditabilidade:** Cada transação é registrada em um *Veritas Ledger* local (logs imutáveis).
4.  **Integridade da Cadeia de Suprimentos:** O pipeline de build adere aos padrões **SLSA Nível 3**.

## 📚 Artefatos de Auditoria
| Categoria | Descrição | Link |
| :--- | :--- | :--- |
| **Arquitetura** | Design Zero Trust e Fluxo de Dados | [Ver](./01-ARCHITECTURE/) |
| **Controles** | Mapeamento ISO e Gestão de Chaves | [Ver](./02-SECURITY-CONTROLS/) |
| **Supply Chain** | SLSA e Gestão de Vulnerabilidades | [Ver](./03-SUPPLY-CHAIN/) |

---
*Gerado pelo Time de Engenharia de Segurança da FoundLab.*