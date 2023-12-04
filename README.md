
### AvalGestMain

## Teste do Contrato para o Smart Contract AvalGestMain

### Configuração Inicial
* Deploy do contrato AvalGestMain. (Pode ser feito utilizando a ferramenta Remix - https://remix-project.org/ ou publicado direto em uma testnet ou produção compativel com EVM)
* Verifique se o endereço do proprietário (owner) é o esperado.

### Atualização de Endereços
* Chame a função `updateManagerAddr` com um novo endereço de carteira para o gerente.
* Verifique se o evento `AddressUpdated` foi emitido corretamente para o gerente.
* Chame a função `updateInvestAddr` com um novo endereço de carteira para o investidor.
* Verifique se o evento `AddressUpdated` foi emitido corretamente para o investidor.
* Chame a função `updateInstitutionAddr` com um novo endereço de carteira para a instituição.
* Verifique se o evento `AddressUpdated` foi emitido corretamente para a instituição.

### Atualização do Montante de Garantia (WarrantyAmount)
* Chame a função `updateWarrantyAmount` com um novo valor para o montante de garantia.
* Verifique se o evento `WarrantyAmountUpdated` foi emitido corretamente.

### Envio de Tokens para o Gerente
* Chame a função `sendToManager` com um montante válido de tokens.
* Verifique se o evento `SentToManager` foi emitido corretamente.
* Verifique se o saldo do investidor é reduzido pelo montante enviado.
* Verifique se o saldo do gerente foi aumentado pelo montante enviado.

### Rescisão do Contrato
* Chame a função `terminationOfContract` como o gerente, especificando o endereço de rescisão como o investidor ou a instituição.
* Verifique se o evento `TerminationOfContract` foi emitido corretamente.
* Verifique se o saldo do gerente é reduzido pelo montante enviado.
* Verifique se o saldo do endereço de rescisão foi aumentado pelo montante enviado.

### Acesso Restrito
* Tente chamar funções restritas (onlyOwner, onlyInvest, onlyManager) com um endereço não autorizado e confirme que as transações são revertidas.

### Atualizações Adicionais
* Tente chamar funções de atualização de endereço e de montante de garantia com um endereço não autorizado e confirme que as transações são revertidas.

*Lembre-se de testar diferentes casos, incluindo valores limite, para garantir a robustez do contrato inteligente. Este roteiro é um ponto de partida e pode ser expandido conforme necessário.*

