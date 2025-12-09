# Gestão de Chaves e Crypto-Shredding

## 1. Criptografia de Envelope
Aderimos estritamente ao padrão de Envelope Encryption:
* **KEK (Chave de Criptografia de Chave):** Armazenada no Cloud KMS (proteção HSM). Propriedade do Cliente.
* **DEK (Chave de Criptografia de Dados):** Gerada por transação em memória volátil.

## 2. Crypto-Shredding (Destruição de Dados)
Para satisfazer o "Direito ao Esquecimento" (LGPD/GDPR):
1.  Mediante solicitação de exclusão, o sistema identifica a versão da KEK associada a um conjunto de dados.
2.  A FoundLab invoca `DestroyCryptoKeyVersion` no KMS do cliente.
3.  **Resultado:** Sem a KEK, qualquer dado residual teórico torna-se matematicamente irrecuperável instantaneamente.

## 3. Gerenciador de Chaves Externo (EKM)
Suporte nativo ao Google Cloud EKM, permitindo que clientes mantenham chaves em HSMs de terceiros (Thales, Fortanix) fora da infraestrutura do Google para soberania absoluta.