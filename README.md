# Análise de Cancelamento de Clientes
Projetos de Machine Learning para investigar em quais momentos do processo os cancelamentos ocorrem, obter insights e apresentar soluções para diminuir a % de cancelamentos.
---
## Base de Dados

A base de dados possui 50.000 linhas e 12 colunas, sendo elas:

| CustomerID | idade | sexo | tempo_como_cliente | frequencia_uso | ligacoes_callcenter |
 dias_atraso | assinatura | duracao_contrato | total_gasto | meses_ultima_interacao | cancelou |

## Visualizar a base de dados

Visualização da base de dados para compreensão das informações relevantes para a análise e se há a necessidade de tratar algum campo por causa do conflito do tipo de dado.

<img width="1102" height="318" alt="image (3)" src="https://github.com/user-attachments/assets/e61350c2-efde-4631-8e51-3a92ca9800d9" />
[Tabela completa exibindo as colunas e o preenchimento dos dados dos clientes.]

## Tratamento de dados

- Removida a coluna CustomerID
<img width="1036" height="323" alt="image (4)" src="https://github.com/user-attachments/assets/2e68718d-c08c-4027-95d2-67da0f5c7222" />
[Tabela completa atualizada após a exclusão da coluna CustomerID.]
---
- Exclusão de linhas vazias da base de dados

Observado que há algumas linhas vazias na base de dados, sendo poucas e portanto não impactando no resultado final, optei pela exclusão.

Essa parte do processo é importante para ser totalmente orientada ao que o dado mostra não correndo o risco de não ter como afirmar algo por falta de um dado em uma das linhas que poderiam dar a base para isso.

<img width="300" height="331" alt="image (5)" src="https://github.com/user-attachments/assets/1edff9eb-9359-49a4-9d12-e99639fcb5a0" />

[Base de dados com linhas vazias]


<img width="300" height="331" alt="image (6)" src="https://github.com/user-attachments/assets/9014e69b-ea09-420a-a177-c5dbd705dd6b" />

[Base de dados com linhas vazias excluídas]

Agora, a base de dados passou a ter 49.996 linhas após a exclusão das linhas vazias ao invés de 50.000 linhas.

## Análise inicial

Neste primeiro momento busca-se entender quantos, em porcentagem, de clientes que cancelaram.

<img width="129" height="116" alt="image (7)" src="https://github.com/user-attachments/assets/fc50520a-b5b2-4af2-8451-8e959f25f5f6" />
[Quantidade de cancelamentos]


<img width="173" height="129" alt="image (8)" src="https://github.com/user-attachments/assets/ea3ef477-d24b-492f-8b3c-c2baf2b8c00b" />
[Proporção de cancelamentos]

Lembrando que 1.0 corresponde aos clientes que cancelaram, totalizando quase 57% (embora não arredondado nesse momento para não perder a precisão do cálculo). E o 0.0 corresponde aos clientes que não cancelaram, totalizando 43%.

## Análise detalhada

Nesta etapa, será compreendido através do retorno dos gráficos qual a causa e como cada coluna impacta no cancelamento dos clientes.

Histogramas

<img width="700" height="437" alt="idade" src="https://github.com/user-attachments/assets/a6b3e53d-5302-4bce-bb63-46990c9d0299" />
<img width="700" height="435" alt="sexo" src="https://github.com/user-attachments/assets/9dbadfc1-fa60-4ade-9be7-7bf1ca9a041e" />
<img width="700" height="434" alt="tempo_como_cliente" src="https://github.com/user-attachments/assets/60f5bf80-de89-4ce1-8f0d-af150efc5afc" />
<img width="700" height="437" alt="frequencia_uso" src="https://github.com/user-attachments/assets/b9a5aec4-8f4c-4fe4-8614-bdde06ebd90d" />
<img width="700" height="435" alt="ligacoes_callcenter" src="https://github.com/user-attachments/assets/fbd328b3-7045-4ddc-aee1-bdfaea59f119" />
<img width="700" height="402" alt="dias_atraso" src="https://github.com/user-attachments/assets/dca307c4-25a5-495c-82ec-ffbd0c1d16b2" />
<img width="700" height="431" alt="assinatura" src="https://github.com/user-attachments/assets/e85e0f78-5c7a-4894-8c96-c664aa97bc22" />
<img width="700" height="430" alt="duracao_contrato" src="https://github.com/user-attachments/assets/b546a46f-f25f-49d5-926a-aa5f9df4574b" />
<img width="700" height="416" alt="total_gasto" src="https://github.com/user-attachments/assets/aabb6fe1-c9cd-4eb6-b91b-b9fbca7110d8" />
<img width="700" height="439" alt="meses_ultima_interacao" src="https://github.com/user-attachments/assets/210f16ea-615f-45b8-90e6-90e21d32c2fd" />
<img width="700" height="429" alt="cancelou" src="https://github.com/user-attachments/assets/4627146d-588f-4990-b14d-b9bbae37888b" />

## Problemas x Soluções Propostas
Histograma duracao_contrato
<img width="700" height="430" alt="duracao_contrato" src="https://github.com/user-attachments/assets/b546a46f-f25f-49d5-926a-aa5f9df4574b" />

*Problema encontrado:* 
- Todos os clientes que assinam o plano mensal cancelam o serviço.

*Solução Proposta:*
- Dar desconto no contrato trimestral ou anual.

Com a implementação dessa solução a taxa de cancelamento cai para 46%.
<img width="120" height="51" alt="image (9)" src="https://github.com/user-attachments/assets/7e556c46-f7b0-4c8d-acda-fc5f5ecc8217" />

Histograma ligacoes_callcenter
<img width="700" height="435" alt="ligacoes_callcenter" src="https://github.com/user-attachments/assets/fbd328b3-7045-4ddc-aee1-bdfaea59f119" />

*Problema encontrado:* 
- A maioria dos clientes que ligaram para o callcenter mais de 4 vezes cancelaram o serviço.

*Solução Proposta:*
- Acionar um alerta vermelho depois que o cliente ligar pela 3ª vez para o callcenter e entrar um time especifico para resolver o problema.

Com a implementação dessa solução a taxa de cancelamento cai para 26%.
<img width="127" height="57" alt="image (10)" src="https://github.com/user-attachments/assets/9f7bd997-b182-4027-9cf4-e3451bbb644f" />

Histograma dias_atraso
<img width="700" height="402" alt="dias_atraso" src="https://github.com/user-attachments/assets/dca307c4-25a5-495c-82ec-ffbd0c1d16b2" />

*Problema encontrado:*
- Se a pessoa passa de 20 dias de atraso no pagamento ela cancela o serviço.

*Solução Proposta:*
- Entrar com um time específico para entrar em contato com o cliente depois de 15 dias de atraso para tentar recuperá-lo.
Após a resolução dos três problemas encontrados, a taxa de cancelamento dos clientes caem para 18%.
<img width="167" height="126" alt="image (11)" src="https://github.com/user-attachments/assets/faf21b9b-4f92-4083-a2b2-2f5d611a014b" />
