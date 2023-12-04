
### AvalGestMain

## Teste do Contrato para o Smart Contract AvalGestMain

### Configuração Inicial
* Deploy do contrato AvalGestMain. (Pode ser feito utilizando a ferramenta Remix - https://remix-project.org/ ou publicado direto em uma testnet ou produção compativel com EVM)
* Verifique se o endereço do proprietário (owner) é o esperado.
* Verifique se as carteiras que serão instituidas como "gerente" e "Investidor" tem saldo para as transações (mínimo 0.1 MATIC em cada)

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

----------------------------------------------------------------

## Teste do Contrato para o Smart Contract AvalGestFiatLoan

### Configuração Inicial
* Deploy do contrato AvalGestFiatLoan.  (Pode ser feito utilizando a ferramenta Remix - https://remix-project.org/ ou publicado direto em uma testnet ou produção compativel com EVM)
* Verifique se o endereço do proprietário (owner) é o esperado.
* Verifique se as carteiras que serão instituidas como "gerente" e "Investidor" tem saldo para as transações (mínimo 0.1 MATIC em cada)

### Atualização de Endereços
* Chame a função `updateManagerAddr` com um novo endereço de carteira para o gerente.
* Verifique se o evento `AddressUpdated` foi emitido corretamente para o gerente.
* Chame a função `updateInvestAddr` com um novo endereço de carteira para o investidor.
* Verifique se o evento `AddressUpdated` foi emitido corretamente para o investidor.
* Chame a função `updateInstitutionAddr` com um novo endereço de carteira para a instituição.
* Verifique se o evento `AddressUpdated` foi emitido corretamente para a instituição.

### Atualização do Montante de Garantia (Warranty Amount)
* Chame a função `updateWarrantyAmount` com um novo valor para o montante de garantia.
* Verifique se o evento `WarrantyAmountUpdated` foi emitido corretamente.

### Solicitação de Contrato
* Chame a função `requestContract` com os parâmetros apropriados.
* Verifique se o evento `RequestContract` foi emitido corretamente.

### Aprovação de Contrato
* Chame a função `approveContract`.
* Verifique se o evento `ApproveContract` foi emitido corretamente.

### Cancelamento de Contrato
* Chame a função `cancelContract`.
* Verifique se o evento `ApproveContract` foi emitido corretamente.

### Rescisão de Contrato
* Chame a função `terminationOfContract`.
* Verifique se o evento `TerminationOfContract` foi emitido corretamente.

### Salvar Recibo de Pagamento
* Chame a função `savePaymentReceipt` com um recibo de pagamento.
* Verifique se o evento `SavePaymentReceipt` foi emitido corretamente.

### Acesso Restrito
* Tente chamar funções restritas (onlyOwner, onlyInvest, onlyManager) com um endereço não autorizado e confirme que as transações são revertidas.

*Lembre-se de testar diferentes casos, incluindo valores limite, para garantir a robustez do contrato inteligente. Este roteiro é um ponto de partida e pode ser expandido conforme necessário.*

-------------------------------------------------------

# Roteiro de Teste para o Smart Contract AvalGestBailInsurance

## 1. Configuração Inicial:

* Deploy do contrato em um ambiente de teste (por exemplo: Remix, Ropsten, Rinkeby, ou Ganache).
Ou faça o deploy do contrato AvalGestBailInsurance.sol em um testnet (Recomendamos a Mumbai)
* Verifique se o endereço do proprietário (owner) é o esperado.
* Verifique se as carteiras que serão usadas no teste têm saldo para as transações


## 2. Verificação dos Parâmetros Iniciais:

- Verificar se o endereço do proprietário (`owner`) é o mesmo que realizou o deploy do contrato.
- Confirmar se os endereços das wallets (`investWallet`, `institutionWallet`, `managerWallet`) foram corretamente inicializados.
- Assegurar que o valor da garantia (`warrantyAmount`) é inicializado como zero.

## 3. Envio de Tokens como Garantia:

- Chamar a função `sendToManagerTokensInCollateral` com um valor adequado de tokens como garantia para a wallet do gerente (`managerWallet`).
- Verificar se o evento `SentToManagerTokensInCollateral` é emitido corretamente.

## 4. Solicitação de Contrato:

- Chamar a função `requestContract` com parâmetros válidos para criar um novo contrato.
- Confirmar se o evento `RequestContract` é emitido corretamente com o status `Pending`.

## 5. Aprovação do Contrato:

- Chamar a função `approveContract` para aprovar o contrato recém-criado.
- Verificar se o evento `ApproveContract` é emitido corretamente com o status `Approved`.

## 6. Cancelamento do Contrato:

- Chamar a função `cancelContract` para cancelar o contrato aprovado.
- Verificar se o evento `ApproveContract` é emitido corretamente com o status `Canceled`.
- Confirmar que os tokens de garantia foram devolvidos à wallet da instituição (`institutionWallet`).

## 7. Finalização do Contrato:

- Chamar a função `completionOfContract` para finalizar o contrato aprovado.
- Verificar se o evento `CompletionOfContract` é emitido corretamente com o status `Finished`.
- Confirmar que os tokens de garantia foram devolvidos à wallet do investidor (`investWallet`).

## 8. Armazenamento do Recibo de Pagamento:

- Chamar a função `savePaymentReceipt` com um recibo de pagamento válido.
- Verificar se o evento `SavePaymentReceipt` é emitido corretamente.

## 9. Atualização de Endereços:

- Chamar as funções `updateManagerAddr`, `updateInvestAddr` e `updateInstitutionAddr` para atualizar os endereços das wallets.
- Confirmar se os eventos `AddressUpdated` são emitidos corretamente para cada atualização.

## 10. Leitura de Contrato e Recibo:

- Chamar as funções `readContract` e `readPaymentReceipt` para verificar se os dados retornados correspondem ao contrato e ao recibo armazenados.

## 11. Atualização do Valor da Garantia:

- Chamar a função `updateWarrantyAmount` para alterar o valor da garantia.
- Verificar se o evento `WarrantyAmountUpdated` é emitido corretamente com o novo valor.

## 12. Testes Adicionais:

- Explorar diferentes caminhos de execução para garantir a robustez do contrato.
- Testar condições de exceção para garantir que o contrato se comporta conforme o esperado em situações anômalas.

## 13. Documentação:

- Verificar se a documentação no GitHub está atualizada e reflete com precisão as funcionalidades e eventos do contrato.

**Observação:** Certifique-se de que a rede de teste escolhida (por exemplo, Ropsten, Rinkeby, Ganache) está configurada corretamente para a execução desses testes.

