# Mapeamento de Compliance ISO 27001:2022

Este documento detalha como o FoundLab Umbrella atende aos controles críticos da ISO.

| Controle ISO | Descrição | Estratégia de Implementação |
| :--- | :--- | :--- |
| **A.8.12** | Prevenção de Vazamento de Dados | **Arquitetura Zero Persistência:** Nenhum dado é gravado em disco. VPC-SC previne exfiltração de rede. |
| **A.8.24** | Uso de Criptografia | **CMEK (Customer-Managed Encryption Keys):** O cliente mantém controle total sobre as chaves de criptografia via Cloud KMS. |
| **A.8.8** | Gestão de Vulnerabilidades Técnicas | **Escaneamento Automatizado:** Artifact Analysis varre imagens diariamente. CVEs Críticas bloqueiam pipelines de deploy. |
| **A.5.15** | Controle de Acesso | **Workload Identity Federation:** Sem chaves de Conta de Serviço de longa duração. Autenticação baseada em tokens de curta duração. |
| **A.8.28** | Codificação Segura | **SLSA Nível 3:** Pipelines de build são herméticos, auditáveis e o código é assinado via Binary Authorization. |