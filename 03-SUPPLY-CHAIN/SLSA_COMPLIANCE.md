# Segurança da Cadeia de Suprimentos de Software (SLSA)

A FoundLab adere ao **SLSA Nível 3** (Supply-chain Levels for Software Artifacts).

## 1. Integridade do Build
* **Builds Herméticos:** Todos os builds rodam no Cloud Build em ambiente isolado e efêmero, sem acesso à internet (exceto repositórios estritamente permitidos).
* **Builds via Código:** Passos de build definidos como código (`cloudbuild.yaml`) e versionados.

## 2. Proveniência e Assinatura
* **Atestado:** Cada build gera um atestado de proveniência assinado.
* **Autorização Binária:** Utilizamos Google Cloud Binary Authorization. A imagem do container é assinada criptograficamente.
* **Política:** O controlador de admissão no ambiente do cliente é configurado para **REJEITAR** qualquer imagem que não carregue uma assinatura válida do KMS da FoundLab.

## 3. Controle de Fonte
* **Revisão por 2 Pessoas:** Todas as alterações de código exigem aprovação de pelo menos um revisor.
* **Histórico Verificado:** Todos os commits são assinados (GPG).