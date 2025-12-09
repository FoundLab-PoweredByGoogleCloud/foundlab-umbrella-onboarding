# Topologia de Rede e Defesa de Perímetro

## 1. VPC Service Controls (VPC-SC)
O Enclave Umbrella deve ser implantado dentro de um Perímetro VPC-SC.
* **Regras de Entrada:** Permitem tráfego apenas da sub-rede específica do Cliente via Private Service Connect.
* **Regras de Saída:** Negam toda saída para internet (`0.0.0.0/0`). Permitem apenas `restricted.googleapis.com` para interação com KMS e Logging.

## 2. Private Service Connect (PSC)
Utilizamos PSC para expor o serviço Umbrella à rede interna do cliente sem necessidade de peering (emparelhamento).
* **Benefício:** Reduz riscos de sobreposição de IP e elimina a necessidade de roteamento transitivo.

## 3. Balanceamento de Carga e TLS
* **Tipo:** Internal HTTP(S) Load Balancer (L7).
* **Política SSL:** Perfil `RESTRICTED` (Apenas TLS 1.2+, cifras fracas desabilitadas).