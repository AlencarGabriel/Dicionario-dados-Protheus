# SC5 - Pedidos de Venda
## SX3 - Campos da tabela

X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|C5_FILIAL|C|2|0|Filial|Filial do Sistema|||||N|||||
02|C5_NUM|C|6|0|Numero|Numero do Pedido|`@X` |`NaoVazio().And.ExistChav("SC5")` |GetSXENum("SC5","C5_NUM")||S|||||
03|C5_TIPO|C|1|0|Tipo Pedido|Tipo de Pedido|`@!` |`Pertence("NCIPDB").and.A410Limpa()` |||N|||N=Normal;C=Compl.Preco/Quantidade;I=Compl.ICMS;P=Compl.IPI;D=Dev.Compras;B=Utiliza Fornecedor||
04|C5_CLIENTE|C|6|0|Cliente|Codigo do Cliente|`@!` |`A410Cli().And.A410ReCalc()` ||SA1|S|||||
05|C5_LOJACLI|C|2|0|Loja|Loja do Cliente|`@!` |`A410Loja().And.A410ReCalc()` |||S|||||
06|C5_CLIENT|C|6|0|Cli.Entrega|Cliente da Entrega|`@!` |`Vazio() .Or. (A410Cli().And.A410ReCalc())` ||SA1|N||||`IIF(M->C5_TIPO$"DB",.F.,.T.)` |
07|C5_LOJAENT|C|2|0|Loja Entrega|Codigo da Loja de Entrega|`@!` |`A410LojEnt()` |||S||||`IIF(M->C5_TIPO$"DB",.F.,.T.)` |
08|C5_TRANSP|C|6|0|Transp.|Codigo da Transportadora|`@X` |`vazio() .or. existcpo("SA4")` ||SA4|N|||||
09|C5_TIPOCLI|C|1|0|Tipo Cliente|Tipo do Cliente|`@!` ||||N|||F=Cons.Final;L=Prod.Rural;R=Revendedor;S=Solidario;X=Exportacao/Importacao||
10|C5_CONDPAG|C|3|0|Cond. Pagto|Condicao de Pagamento|`@!` |`ExistCpo("SE4").And.A410AcrFin().And.MaVldTabPrc(M->C5_TABELA,M->C5_CONDPAG,,M->C5_EMISSAO) .And. A410Recalc()` ||SE4|N|||||
11|C5_TABELA|C|3|0|Tabela|Codigo da Tabela de Preco||`MaVldTabPrc(M->C5_TABELA,M->C5_CONDPAG,,M->C5_EMISSAO) .And. A410ReCalc()` ||DA0|N|||||
12|C5_VEND1|C|6|0|Vendedor 1|Codigo do Vendedor 1|`@X` |`a410Vend() .Or. Vazio()` ||SA3|N|||||
13|C5_COMIS1|N|5|2|Comissao 1|Comissao do Vendedor 1|`@E 99.99` |`positivo() .or. vazio()` |||N|||||
14|C5_VEND2|C|6|0|Vendedor 2|Codigo do Vendedor 2|`@X` |`a410Vend() .Or. Vazio()` ||SA3|N|||||
15|C5_COMIS2|N|5|2|Comissao 2|Comissao do Vendedor 2|`@E 99.99` |`positivo() .or. vazio()` |||N|||||
16|C5_VEND3|C|6|0|Vendedor 3|Codigo do Vendedor 3|`@X` |`a410Vend() .Or. Vazio()` ||SA3|N|||||
17|C5_COMIS3|N|5|2|Comissao 3|Comissao do Vendedor 3|`@E 99.99` |`positivo() .or. vazio()` |||N|||||
18|C5_VEND4|C|6|0|Vendedor 4|Codigo do Vendedor 4|`@X` |`a410Vend() .Or. Vazio()` ||SA3|N|||||
19|C5_COMIS4|N|5|2|Comissao 4|Comissao do Vendedor 4|`@E 99.99` |`positivo() .or. vazio()` |||N|||||
20|C5_VEND5|C|6|0|Vendedor 5|Codigo do Vendedor 5|`@X` |`a410Vend() .Or. Vazio()` ||SA3|N|||||
21|C5_COMIS5|N|5|2|Comissao 5|Comissao do Vendedor 5|`@E 99.99` |`positivo() .or. vazio()` |||N|||||
22|C5_DESC1|N|5|2|Desconto 1|Desconto 1|`@E 99.99` |`(Positivo() .or. vazio()) .and. a410Recalc()` |||N|||||
23|C5_DESC2|N|5|2|Desconto 2|Desconto 2|`@E 99.99` |`(Positivo() .or. vazio()) .and. a410Recalc()` |||N|||||
24|C5_DESC3|N|5|2|Desconto 3|Desconto 3|`@E 99.99` |`(Positivo() .or. vazio()) .and. a410Recalc()` |||N|||||
25|C5_DESC4|N|5|2|Desconto 4|Desconto 4|`@E 99.99` |`(Positivo() .or. vazio()) .and. a410Recalc()` |||N|||||
26|C5_BANCO|C|3|0|Banco|Codigo do Banco|`@!` |`Vazio() .or. Existcpo("SA6")` ||BCO|N|||||
27|C5_DESCFI|N|5|2|Desc.Financ.|Desconto Financeiro|`@E 99.99` |`positivo() .or. vazio()` |||N|||||
28|C5_EMISSAO|D|8|0|DT Emissao|Data da Emissao||`MaVldTabPrc(M->C5_TABELA,M->C5_CONDPAG,,M->C5_EMISSAO)` |ddatabase||N|||||
29|C5_COTACAO|C|6|0|Licitacao|Numero da Licitacao|`@X` |||AH9|N|||||
30|C5_PARC1|N|12|2|Parcela 1|Valor da Parcela 1|`@E 999,999,999.99` |`positivo() .or. vazio()` |||N|||||
31|C5_DATA1|D|8|0|Vencimento 1|Vencimento da Parcela 1||`A410Venc()` |||N|||||
32|C5_PARC2|N|12|2|Parcela 2|Valor da Parcela 2|`@E 999,999,999.99` |`positivo() .or. vazio()` |||N|||||
33|C5_DATA2|D|8|0|Vencimento 2|Vencimento da Parcela 2||`A410Venc()` |||N|||||
34|C5_PARC3|N|12|2|Parcela 3|Valor da Parcela 3|`@E 999,999,999.99` |`positivo() .or. vazio()` |||N|||||
35|C5_DATA3|D|8|0|Vencimento 3|Vencimento da Parcela 3||`A410Venc()` |||N|||||
36|C5_PARC4|N|12|2|Parcela 4|Valor da Parcela 4|`@E 999,999,999.99` |`positivo() .or. vazio()` |||N|||||
37|C5_DATA4|D|8|0|Vencimento 4|Vencimento da Parcela 4||`A410Venc()` |||N|||||
38|C5_TPFRETE|C|1|0|Tipo Frete|Tipo do Frete Utilizado|`X` |`pertence("CFTRDS")` |||N|||C=CIF;F=FOB;T=Por conta terceiros;R=Por conta remetente;D=Por conta destinatário;S=Sem frete||
39|C5_FRETE|N|12|2|Frete|Valor do Frete|`@E 999,999,999.99` |`positivo() .or. vazio()` |||N|||||
40|C5_SEGURO|N|12|2|Seguro|Valor do Seguro|`@E 999,999,999.99` |`positivo() .or. vazio()` |||N|||||
41|C5_DESPESA|N|14|2|Despesa|Valor Despesa Acessoria|`@E 99,999,999,999.99` ||||N|||||
42|C5_FRTCFOP|C|5|0|Frete CFOP|CFOP Referente ao Frete|||||N|A|R|||
43|C5_FRETAUT|N|12|2|Frete Auton.|Frete Autonomo|`@E 999,999,999.99` |`positivo()` |||N|||||
44|C5_REAJUST|C|3|0|Tipo Reajust|Tipo de Reajuste Usado|`@X` |`Vazio().Or.ExistCpo("SM4")` ||SM4|N|||||
45|C5_MOEDA|N|2|0|Moeda|Moeda do Pedido de Venda|`@E 99` |`M->C5_MOEDA > 0 .AND. M->C5_MOEDA <= MOEDFIN() .And. a410Recalc()` |1||N|||||
46|C5_PESOL|N|11|4|Peso Liquido|Peso Liquido|`@E 999,999.9999` |`positivo() .or. vazio()` |||N|||||
47|C5_PBRUTO|N|11|4|Peso Bruto|Peso Bruto|`@E 999,999.9999` |`positivo() .or. vazio()` |||N|||||
48|C5_REIMP|N|1|0|Qt Pre-Notas|Quant. Pre-Notas Impr.|`9` ||||N|||||
49|C5_REDESP|C|6|0|Redespacho|Codigo Transp. Redespacho|`@X` |`Vazio().Or.ExistCpo("SA4")` ||SA4|N|||||
50|C5_VOLUME1|N|5|0|Volume 1|Qtde de Volumes tipo 1|`99999` |`positivo() .or. vazio()` |||N|||||
51|C5_VOLUME2|N|5|0|Volume 2|Qtde de Volumes tipo 2|`99999` |`positivo() .or. vazio()` |||N|||||
52|C5_VOLUME3|N|5|0|Volume 3|Qtde de Volumes tipo 3|`99999` |`positivo() .or. vazio()` |||N|||||
53|C5_VOLUME4|N|5|0|Volume 4|Qtde de Volumes tipo 4|`99999` |`positivo() .or. vazio()` |||N|||||
54|C5_ESPECI1|C|10|0|Especie 1|Especie do Volume tipo 1|`@X` ||||N|||||
55|C5_ESPECI2|C|10|0|Especie 2|Especie do Volume tipo 2|`@X` ||||N|||||
56|C5_ESPECI3|C|10|0|Especie 3|Especie do Volume tipo 3|`@X` ||||N|||||
57|C5_ESPECI4|C|10|0|Especie 4|Especie do Volume tipo 4|`@X` ||||N|||||
58|C5_ACRSFIN|N|6|2|Acr. Financ|Acrescimo Financeiro|`@E 999.99` |`positivo() .or. vazio()` |||N|||||
59|C5_MENNOTA|C|60|0|Mens.p/ Nota|Mensagem para Nota Fiscal|`@S45` |`Vazio().Or.A410MenNo()` |||N|||||
60|C5_MENPAD|C|3|0|Mens. Padrao|Mensagem Padrao 1|`@!` |`Vazio().Or.ExistCpo("SM4")` ||SM4|N|||||
61|C5_INCISS|C|1|0|ISS Incluso|ISS incluso no Preço|`@!` ||||N|||S=Sim;N=Nao||
62|C5_LIBEROK|C|1|0|Liber. Total|Pedido Liberado Total|`@!` ||||N|||||
63|C5_OK|C|2|0|OK|OK|||||N|||||
64|C5_NOTA|C|9|0|Nota Fiscal|Numero da Nota Fiscal|`@!` ||||N|||||
65|C5_SERIE|C|3|0|Serie|Serie da Nota Fiscal|`!!!` ||||N|||||
66|C5_KITREP|C|6|0|Kit Reparo|Codigo do Kit de Reparo|`@!` |`A410KitRep(M->C5_KITREP)` ||SO4|N|||||
67|C5_OS|C|6|0|Gerado p/ OS|Numero da OS geradora|`@!` ||||N|||||
68|C5_TIPLIB|C|1|0|Tp Liberação|Tipo de Liberação|`@!` |`Pertence("12")` |"1"||N|||1=Libera por Item;2=Libera por Pedido||
69|C5_DESCONT|N|14|2|Indenizacao|Desconto de Indenizacao|`@E 99,999,999,999.99` |||||||||
70|C5_PEDEXP|C|20|0|Proc.Export.|Processo de Exportacao|`@!` ||||S|V||||
71|C5_TXMOEDA|N|11|4|Taxa Moeda|Taxa da Moeda|`@E 999999.9999` ||1||N|||||
72|C5_TPCARGA|C|1|0|Carga|Carga|`@!` |`Pertence('12')` |'2'||N|||1=Utiliza;2=Nao utiliza||
73|C5_DTLANC|D|8|0|Dt.Contab.|Data de Contabilização|||||N|V|R|||
74|C5_PDESCAB|N|5|2|%Indenizacao|Percentual de indenizacao|`@e 99.99` |`Positivo()` |||N|||||
75|C5_BLQ|C|1|0|Blq. Regras|Bloqueio de Regras|`@!` ||||N|V|R|||
76|C5_FORNISS|C|6|0|Forn.ISS|Fornecedor de ISS|`@!` |`ExistCpo("SA2", M->C5_FORNISS)` ||SA2||||||
77|C5_CONTRA|C|10|0|Contrato|Numero do contrato|`@!` ||||N|||||
78|C5_KM|N|7|0|Dist.Entrega|Distancia de Entrega|`@E 9,999,999` |`Positivo() .And. a410FreteP()` |||N|A|V|||
79|C5_VLR_FRT|N|12|2|Frete Pauta|Valor do Frete de Pauta|`@E 999,999,999.99` |`Positivo() .Or. Vazio()` |||N|A|R|||
80|C5_MDCONTR|C|15|0|Num.Contrato|Numero do Contrato|`@!` ||||N|V|R|||
81|C5_MDNUMED|C|6|0|Num.Medicao|Numero da Medicao|`@!` ||||N|V|R|||
82|C5_GERAWMS|C|1|0|Gera OS.WMS|Gera O.S./WMS|`@!` |`Pertence("123")` |"1"||N|A||1=No pedido;2=Na Montagem da Carga;3=Na Unitização da Carga||
83|C5_MDPLANI|C|6|0|Num.Planilha|Numero da Planilha|`@!` ||||N|V|R|||
84|C5_SOLFRE|C|2|0|Sol. Frete|Solicitação de Frete|`@!` |||||||||
85|C5_FECENT|D|8|0|Dt. Entrega|Data de Entrega|||||N|A|R|||
86|C5_SOLOPC|C|1|0|Opc Cliente|Usa Opcionais do Cliente|`@!` ||"1"||N|A|R|1=Nao;2=Sim||
87|C5_SUGENT|D|8|0|Dt. Sug. Ent|Data sugerida de entrega|||||N|V|R|||
88|C5_CODED|C|15|0|Cod. Edital|Codigo do Edital|`@!` ||||S|V|R|||
89|C5_NUMPR|C|15|0|Nr. Processo|Numero Processo|`@!` ||||S|V|R|||
90|C5_ORCRES|C|6|0|Num. Orcam.|Numero do Orcamento|||||N|A|R|||
91|C5_RECFAUT|C|1|0|Pag.Fret.Aut|Pagto do frete autonomo|`@!` |`Pertence("12") .And. MaFisGet("NF_RECFAUT")` |||||R|1=Emitente;2=Transportador||
92|C5_RECISS|C|1|0|Recolhe ISS?|Recolhe ISS?|`@!` |`Pertence("12") .And. MaFisGet("NF_RECISS")` |||N|A|R|1=Sim;2=Não||
93|C5_ESTPRES|C|2|0|UF. Prest.|UF Prestação|`@!` |`Vazio() .or. ExistCpo("SX5","12"+M->C5_ESTPRES)` ||12|S|A|R|||
94|C5_OBRA|C|10|0|Cod. Obra|Codigo da Obra|`@!` ||||S|A|R|||
95|C5_CLIREM|C|6|0|Cli. Remessa|Cliente da Remessa|`@!` |`Vazio() .Or. ExistCpo("SA1")` ||SA1|N||||`IIF(M->C5_TIPO$"DB",.F.,.T.)` |
96|C5_LOJAREM|C|2|0|Loja Remessa|Codigo da loja de Remessa|`@!` |`Vazio() .Or. ExistCpo("SA1",M->C5_CLIREM+M->C5_LOJAREM)` |||N||||`IIF(M->C5_TIPO$"DB",.F.,.T.)` |
97|C5_MUNPRES|C|7|0|Mun.Prest.|Municipio de Prestação|`@!` |||CC2SC5|S|A|R|||
98|C5_NATUREZ|C|10|0|Natureza|Natureza||`Existcpo("SED") .And. MafisGet("NF_NATUREZA")` ||SED||||||
99|C5_NUMENT|C|9|0|Entrega|Número da Entrega|`@9` ||||N|||||
A0|C5_ORIGEM|C|15|0|Origem|Origem do Pedido|`@!` |||||V||||
A1|C5_REMCTR|C|15|0|Contrato Rem|Nro Contrato Ref Remessa|`@!` ||||N||R||`.F.` |
A2|C5_REMREV|C|3|0|Revisao Ctr|Nro Revisão Ctr. Remessa|`@!` ||||N|V|R||`.F.` |
A3|C5_TABTRF|C|3|0|Tabela Trf.|Tab Transf de IPI|`@!` |`Vazio().Or.ExistCpo("DA0")` ||DA0|N|A|R|||
A4|C5_TPCOMPL|C|1|0|Tipo Compl.|Tipo de Complemento|`@!` |`Pertence("12") .And. A410Limpa()` |"1"||N|A|R|1=Preço; 2=Quantidade||
A5|C5_CODEMB|C|4|0|Cod. Embarc.|Código da Embarcação|`9999` |`ExistCpo("D31", M->C5_CODEMB) .OR. Vazio(M->C5_CODEMB)` |||S|A|R||`Val(M->C5_MODANP) = 4` |
A6|C5_VEICULO|C|8|0|Veic. Transp|Veiculo do Transporte|`@!` |`Vazio().Or.ExistCPO("DA3")` ||DA3||||||
A7|C5_DESCMUN|C|30|0|Desc.Mun.|Descrição Mun.Prest.|`@!` ||||S|A|R|||
A8|C5_CODMOT|C|11|0|Cod.Motorist|Cod. do Motorista|`@R 999.999.999-99` |`EXISTCPO("DHB",M->C5_CODMOT) .AND. DCLVV003 ()` |||N|A|R|||
A9|C5_CODSAF|C|15|0|Cod. Safra|Código da Safra|`@!` |`Vazio() .Or. ExistCpo('NJU')` ||NJU|N|A|R|||
B0|C5_CODVGLP|C|6|0|Cod.Vas.GLP|Código do Vasilhame GLP|`999999` |`ExistCpo("SX5", "HL"+M->C5_CODVGLP) .OR. VAZIO(M->C5_CODVGLP)` ||HL|N|A|R|||
B1|C5_CLIRET|C|6|0|Cli.Retirada|Cliente de Retirada|`@!` |`ExistCpo("SA1")` ||SA1|N|A|R||`IIF(M->C5_TIPO$'D',.F.,.T.)` |
B2|C5_CMUNDE|C|5|0|Mun.Dest|Mun.Dest|`@99999` |`Vazio() .Or. ExistCpo("CC2",M->C5_UFDEST+M->C5_CMUNDE)` ||CC2|N|A|R|||
B3|C5_CMUNOR|C|5|0|Mun.Origem|Mun.Origem|`@99999` |`Vazio() .Or. ExistCpo("CC2",M->C5_UFORIG+M->C5_CMUNOR)` ||CC2|N|A|R|||
B4|C5_CNO|C|6|0|Cod CNO|Codigo CNO||`Vazio() .Or.(ExistCpo('SON',M->C5_CNO ) .And. a410VldPMS())` ||SON|N|A|R|||
B5|C5_CGCINT|C|14|0|CNPJ/CPF|CNPJ/CPF|`@!` ||||S|A|R|||
B6|C5_CLIINT|C|40|0|Razao Int.|Razao Intermediario|`@!` ||||S|A|R|||
B7|C5_DTTXREF|D|8|0|Dt.R.Cambial|Data Referencia Cambial|||||N|V|R|||
B8|C5_ECPRESN|C|1|0|Ped.Presente|Pedido Presente|`@!` ||||N|A|R|||
B9|C5_ECSEDEX|C|13|0|Sedex EC|Sedex E-Commerce|`@!` ||||N|A|R|||
C0|C5_ECVINCU|C|6|0|Sedex EC|Sedex E-Commerce|`@!` ||||N|V|R|||
C1|C5_FILGCT|C|2|0|Filial GCT|Filial Matriz Contrato|||||N||R|||
C2|C5_LOJARET|C|2|0|Lj. Retirada|Loja de Retirada|`@!` |`ExistCpo("SA1",M->C5_CLIRET+M->C5_LOJARET)` |||N|A|R||`IIF(M->C5_TIPO$'D',.F.,.T.)` |
C3|C5_IMINT|C|18|0|Insc.mun.|Inscricao municipal|`@!` ||||S|A|R|||
C4|C5_INDPRES|C|1|0|Presença Com|Presença Comprador|`@!` |`Pertence(" 0/1/2/3/5/9")` |||S|A|R|0=Não Aplica;1=Presencial;2=Não Presencial,Net;3=Não Presencial,TeleAtendi.;5=Presencial,ForadoEstab.;9=Não Presencial,outros||
C5|C5_TXREF|N|11|4|Taxa Cambial|Taxa Cambial|`@E 999,999.9999` |`positivo()` |||S|V|R|||
C6|C5_UFDEST|C|2|0|UF Destino|UF Destino|`@!` |||12|N|A|R|||
C7|C5_UFORIG|C|2|0|UF Origem|UF Origem|`@!` |||12|N|A|R|||
C8|C5_TIPOBRA|C|1|0|Tipo Obra|Tipo da Obra|`@!` |`pertence("123")` |||N|A|R|1=Minha Casa Minha Vida;2=Regime Presumido;3=Regime Ordinário||
C9|C5_RET20G|C|1|0|Ret.20 Graus|Retorno a 20 Graus.?|`@!` |`Pertence("SN")` |"N"||N|A|R|S=Sim;N=Não||
D0|C5_SDOC|C|3|0|Série Doc.|Série do Documento Fiscal|`!!!` ||||N|V|R|||
D1|C5_SDOCSUB|C|3|0|Série Subst.|Série da Nf Substituída|`!!!` ||||N|V|R|||
D2|C5_STATUS|C|2|0|Status Ecom.|Status E-Commerce|`@!` ||||N|V|R|00=Gerado; 05=Em analise; 10=Pagamento confirmado; 15=Embalado; 21=Parcialmente enviado; 30=Enviado; 90=cancelado; 91=Devolvido||
D3|C5_SERSUBS|C|3|0|Serie Subst.|Serie da Nf Substituída|`!!!` ||||S|A|R|||
D4|C5_SLENVT|C|1|0|Sol.Env.Seg.|Sol.Env.Amost.-Testemunho|`@!` |`Pertence("12")` |"2"||S|A|R|1=Sim;2=Nao||
D5|C5_PLACA1|C|7|0|Truck/Cavalo|Placa do Truck/Cavalo|`@R AAA-9999` |`DCLVV001()` |||N|A|R|||
D6|C5_PLACA2|C|7|0|Carreta|Placa da Carreta|`@R AAA-9999` |`DCLVV002()` |||N|A|R|||
D7|C5_PREPEMB|C|1|0|Status Embar|Status do embarque|||||N|A|R|0=Nao;1=Sim||
D8|C5_RASTR|C|20|0|Rastreio|Rastreio do Pedido E-com.|`@!` ||||N|A|R|||
D9|C5_PEDECOM|C|10|0|Ped E-Com.|Pedido E-Commerce|`@!` ||||N|V|R|||
E0|C5_NTEMPEN|C|22|0|Nt Empenho|Ident. Nota Empenho|`@!` ||||S|A|R|||
E1|C5_NFSUBST|C|9|0|Nf Subst|NF Substituída|`@!` ||||S|A|R|||
E2|C5_NOMMOT|C|30|0|Nome Motoris|Nome do Motorista|`@!` ||IF(!INCLUI,Posicione("DHB",1,xFilial("DHB")+SC5->C5_CODMOT,"DHB_NOMMOT"),"")||N|V|V|||
E3|C5_MODANP|C|2|0|Modal ANP|Via de transp. Modal ANP|`99` |`ExistCpo("SX5", "HA"+M->C5_MODANP) .OR. Vazio(M->C5_MODANP)` ||HA|N|A|R|||
E4|C5_MOEDTIT|N|2|0|Moeda Titulo|Moeda do titulo|`99` ||||S|A|R|||
E5|C5_MSBLQL|C|1|0|Status|Status do registro|`@!` |`Pertence("12")` |"2"|||A|R|1=Inativo;2=Ativo||
E6|C5_VOLTAPS|C|1|0|Volta Passo|Volta passo de Status|`@!` ||||N|V|R|1=Sim;2=Não||
E7|C5_TRCNUM|C|15|0|Ac. Troca|Número do Acordo de Troca|`@!` |`Vazio() .Or. ExistCpo('NKT')` |||N|V|R|||
E8|C5_ARTOBRA|C|15|0|Código ART|ART da Obra|`@!` ||||N|A|R|||


## SIX - Índices da tabela

ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|C5_FILIAL+C5_NUM|Numero|||S|
2|C5_FILIAL+DTOS(C5_EMISSAO)+C5_NUM|DT Emissao + Numero|||S|
3|C5_FILIAL+C5_CLIENTE+C5_LOJACLI+C5_NUM|Cliente + Loja + Numero|CLI||S|
4|C5_FILIAL+C5_OS|Gerado p/ OS|||S|
5|C5_FILIAL+C5_NUMENT|Entrega|||S|
6|C5_FILIAL+C5_CODED+C5_NUMPR|Cod. Edital + Nr. Processo|||S|
7|C5_FILIAL+C5_CODEMB|Cod. Embarc.|||S|
8|C5_FILIAL+C5_MODANP|Modal ANP|||S|
9|C5_FILIAL+C5_CODVGLP|Cod.Vas.GLP|||S|


