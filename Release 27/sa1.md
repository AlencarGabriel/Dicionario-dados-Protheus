# SA1 - Clientes
## SX3 - Campos da tabela

X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|A1_FILIAL|C|2|0|Filial|Filial do Sistema|||||N||R|||
02|A1_COD|C|6|0|Codigo|Codigo do Cliente|`@!` |`IIF(Empty(M->A1_LOJA),.T.,ExistChav("SA1",M->A1_COD+M->A1_LOJA,,"EXISTCLI")) .And. FatVldStr()` |||S||||`A030WHEN()` |
03|A1_LOJA|C|2|0|Loja|Loja do Cliente|`@!` |`Iif(GetNewPar("MV_CLASSIS",.F.),.T.,EXISTCHAV("SA1",M->A1_COD+M->A1_LOJA,,"EXISTCLI"))` |||S|||||
04|A1_NOME|C|40|0|Nome|Nome do cliente|`@!` |`FatVldStr()` |||S|||||
05|A1_PESSOA|C|1|0|Fisica/Jurid|Pessoa Fisica/Juridica|`@!` |`Pertence(" FJ")` |||N|||F=Fisica;J=Juridica||
06|A1_NREDUZ|C|20|0|N Fantasia|Nome Reduzido do cliente|`@!` ||||S|||||
07|A1_END|C|80|0|Endereco|Endereco do cliente|`@!` ||||N|||||
08|A1_BAIRRO|C|40|0|Bairro|Bairro do cliente|`@S15` ||||N|||||
09|A1_TIPO|C|1|0|Tipo|Tipo do Cliente|`@!` ||||S|||F=Cons.Final;L=Produtor Rural;R=Revendedor;S=Solidario;X=Exportacao||
10|A1_EST|C|2|0|Estado|Estado do cliente|`@!` |`ExistCpo("SX5","12"+M->A1_EST) .AND. IE(M->A1_INSCR,M->A1_EST)` ||12|N|||||
11|A1_ESTADO|C|20|0|Nome Estado|Nome do Estado Fornecedor|`@!S20` ||||N|||||
12|A1_COD_MUN|C|5|0|Cd.Municipio|Código do Municipio||`ExistCpo("CC2",M->A1_EST+M->A1_COD_MUN)` ||CC2SA1|N|||||
13|A1_CEP|C|8|0|CEP|Cod Enderecamento Postal|`@R 99999-999` |`A030Cep()` |||N|||||
14|A1_MUN|C|60|0|Municipio|Municipio do cliente|`@!` ||||N|||||
15|A1_REGIAO|C|3|0|Regiao|Regiao do Cliente|`@!` |`Vazio() .OR. ExistCpo("SX5","A2"+M->A1_REGIAO)` ||A2|N|A|R|||
16|A1_DSCREG|C|15|0|Desc.Região|Descrição da Região|`@!` |||||V|R|||
17|A1_NATUREZ|C|10|0|Natureza|Codigo da Nat Financeira|`@!` |`FinVldNat( .T., , 1 )` ||SED|N|||||
18|A1_IBGE|C|11|0|Cod.IBGE|Codigo do IBGE|`@!` |`FS_VLCIDEST(4).and.(vazio().or.ExistCpo("VAM"))` ||AM1|N|A|R|||
19|A1_ENDCOB|C|40|0|End.Cobranca|End.de cobr. do cliente|`@!` ||||N|||||
20|A1_DDI|C|6|0|DDI|Codigo do DDI|`999999` |`IIF(!EMPTY(M->A1_DDI), ExistCpo("ACJ",M->A1_DDI),.T.)` ||ACJ|N|||||
21|A1_DDD|C|3|0|DDD|Codigo do DDD|`999` ||||N|||||
22|A1_ENDENT|C|40|0|End.Entrega|End.de entr. do cliente|`@!` ||||N|||||
23|A1_ENDREC|C|40|0|End.Recebto|End.de Receb. do cliente|`@!` ||||N|||||
24|A1_COMPENT|C|50|0|Comp Entrega|Compl. do End. de Entrega|`@!` ||||N|A||||
25|A1_TEL|C|15|0|Telefone|Telefone do cliente|`@R 999999999999999` ||||N|||||
26|A1_TRIBFAV|C|1|0|Pes.Tri.Fav.|Pessoa Trib. Favor.|`@!` |`Pertence (" 12")` |||N|A||1=Sim;2=Não||
27|A1_CONTATO|C|15|0|Contato|Nome do Contato|`@x` ||||N|A||||
28|A1_FAX|C|15|0|FAX|Numero do FAX do cliente|`@R 999999999999999` ||||N|||||
29|A1_CGC|C|14|0|CNPJ/CPF|CNPJ/CPF do cliente|`@R 99.999.999/9999-99` |`Vazio() .Or. IIF( M->A1_TIPO == "X", .T., (CGC(M->A1_CGC) .And. A030CGC(M->A1_PESSOA, M->A1_CGC) .And. A030VldUCod() ))` |||S|||||
30|A1_INSCR|C|18|0|Ins. Estad.|Inscricao Estadual|`@!` |`IE(M->A1_INSCR,M->A1_EST) .And. A030VldUCod()` |||N|||||
31|A1_PFISICA|C|18|0|RG/Ced.Estr.|Reg.Geral/Ced.Estrangeiro|`@!` |`A030VldUCod()` |||N|||||
32|A1_TELEX|C|10|0|Telex|Telex do cliente|||||N|||||
33|A1_PAIS|C|3|0|Pais|Codigo do País|`@!` |`Vazio() .or. ExistCpo("SYA",M->A1_PAIS)` ||SYA|N|||||
34|A1_INSCRM|C|18|0|Ins. Municip|Inscricao Municipal|`@!` ||||N|||||
35|A1_PAISDES|C|25|0|Descr. Pais|Descr. Pais|`@!` ||E_Field("A1_PAIS","YA_DESCR")||N|V|V|||
36|A1_VEND|C|6|0|Vendedor|Codigo do Vendedor|`@!` |`Vazio() .or. ExistCPO("SA3", M->A1_VEND, 1)` |IIF(FINDFUNCTION("CRMXINTVEND"),CRMXINTVEND(),"")|SA3|N|A|R|||
37|A1_COMIS|N|5|2|% Comissao|Aliquota de Comissao|`@E 99.99` ||||N|||||
38|A1_CONTA|C|20|0|C. Contabil|Conta Contabil do cliente|`@!` |`vazio().or. Ctb105Cta()` ||CT1|N|||||
39|A1_BCO1|C|3|0|Banco 1|BANCO 1|`@!` |||BC8|N|||||
40|A1_BCO2|C|3|0|Banco 2|BANCO 2|`@!` |||BC8|N|||||
41|A1_BCO3|C|3|0|Banco 3|BANCO 3|`@!` |||BC8|N|||||
42|A1_BCO4|C|3|0|Banco 4|BANCO 4|`@!` |||BC8|N|||||
43|A1_BCO5|C|3|0|Banco 5|BANCO 5|`@!` |||BC8|N|||||
44|A1_TRANSP|C|6|0|Transp.|Codigo da Transportadora|`@!` |`vazio().or.existcpo("SA4")` ||SA4|N|||||
45|A1_TPFRET|C|1|0|Tipo Frete|Tipo de Frete do cliente|`@!` |`pertence("CFTRDS")` |||N|||C=CIF;F=FOB;T=Por conta terceiros;R=Por conta remetente;D=Por conta destinatário;S=Sem frete||
46|A1_COND|C|3|0|Cond. Pagto|Condicao de Pagamento|`@!` |`Vazio().Or.ExistCpo("SE4")` ||SE4|N|||||
47|A1_DESC|N|2|0|Desconto|Desconto ao cliente|`99` ||||N|||||
48|A1_PRIOR|C|1|0|Prioridade|Prioridade do cliente|`9` ||||N|||||
49|A1_RISCO|C|1|0|Risco|Grau de Risco do cliente|`@!` ||||S|||A=Risco A;B=Risco B;C=Risco C;D=Risco D;E=Risco E||
50|A1_LC|N|14|2|Lim. Credito|Limite de Cred.do cliente|`@E 999,999,999.99` ||||N|||||
51|A1_VENCLC|D|8|0|Venc.Lim.Cre|Vencimento do Lim. Credit|||||N|||||
52|A1_CLASSE|C|1|0|Classe Cred.|Classe de Credito|`@!` |`Pertence("ABC")` |||N|||A=Classe A;B=Classe B;C=Classe C||
53|A1_LCFIN|N|14|2|Lim Cred Sec|Lim Credito Secundario|`@E 999,999,999.99` ||||N|||||
54|A1_MOEDALC|N|2|0|Moeda do LC|Moeda do Limite de credit|`99` |`M->A1_MOEDALC <= MoedFin() .And. Positivo()` |VAL(GetMV("MV_MCUSTO"))||N|||||
55|A1_MSALDO|N|16|2|Maior Saldo|Maior Saldo do cliente|`@E 9,999,999,999,999.99` ||||N|V||||
56|A1_MCOMPRA|N|16|2|Maior Compra|Maior Compra do cliente|`@E 9,999,999,999,999.99` ||||N|V||||
57|A1_METR|N|7|2|Media Atraso|Méd.de atrasos do cliente|`@E 9999.99` ||||N|V||||
58|A1_PRICOM|D|8|0|1a Compra|Data 1a Compra do cliente|||||N|V||||
59|A1_ULTCOM|D|8|0|Ult. Compra|Data da ultima Compra|||||N|||||
60|A1_NROCOM|N|5|0|Nro Compras|Nro de compras do cliente|`99999` ||||N|V||||
61|A1_FORMVIS|C|3|0|Form. Visita|Formula da Visita||`ExistCpo("SM4").Or.Vazio()` ||SM4|N|||||
62|A1_TEMVIS|N|3|0|Freq.Visitas|Frequencia de Visitas|`999` ||||N|||||
63|A1_ULTVIS|D|8|0|Ult. Visita|Data da ultima Visita|||||N|||||
64|A1_TMPVIS|C|5|0|Tempo Visita|Tempo da Visita|`99:99` ||"00:00"||N|||||
65|A1_TMPSTD|C|5|0|Tempo Padrao|Tempo Padrao p/Deslocam.|`99:99` ||"00:00"||N|||||
66|A1_CLASVEN|C|1|0|Classif.Vend|Classificacao de Vendas|`@!` |`Pertence("ABC")` |||N|||A=Classe A;B=Classe B;C=Classe C||
67|A1_MENSAGE|C|3|0|Mensagem|Mensagem do cliente||||SM4|N|||||
68|A1_SALDUP|N|16|2|Saldo Titulo|Saldo Duplic. do cliente|`@E 9,999,999,999,999.99` ||||N|V||||
69|A1_RECISS|C|1|0|Recolhe ISS|Recolhe ISS             ?|`@!` |`Pertence("12 ")` |||N|||1=Sim;2=Nao||
70|A1_NROPAG|N|4|0|Nro Pagtos|Nro de Pagtos do cliente|`9999` ||||N|V||||
71|A1_SALPEDL|N|16|2|Sld Ped. Lib|Saldo Pedidos Liberados|`@E 9,999,999,999,999.99` ||||N|V||||
72|A1_TRANSF|C|1|0|Transf. Arq.|Flag p/transf. arquivos|`!` ||||N|||||
73|A1_SUFRAMA|C|12|0|SUFRAMA|Codigo na SUFRAMA|||||N|||||
74|A1_ATR|N|16|2|Atrasados|Valor dos Atrasos|`@E 9,999,999,999,999.99` ||||N|V||||
75|A1_VACUM|N|16|2|Vlr.Acumul.|Valor Acum. Vendas no Ano|`@E 9,999,999,999,999.99` ||||N|V||||
76|A1_SALPED|N|16|2|Saldo Pedido|Saldo de Pedidos|`@E 9,999,999,999,999.99` ||||N|V||||
77|A1_TITPROT|N|3|0|Tit.Protest.|Titulos Protestados|`999` ||||N|||||
78|A1_CHQDEVO|N|3|0|Cheques Dev.|Numero de Cheques Devolv.|`999` ||||N|||||
79|A1_DTULTIT|D|8|0|Ult.Protesto|Data do Ult. Titulos Dev.|||||N|||||
80|A1_DTULCHQ|D|8|0|DT.Dev.Cheq.|Dt.de Devol. Ult. Cheque|||||N|||||
81|A1_MATR|N|4|0|Maior Atraso|Maior atraso do cliente|`9999` ||||N|V||||
82|A1_MAIDUPL|N|16|2|Maior Dupl.|Valor da maior Duplicata|`@E 9,999,999,999,999.99` ||||N|V||||
83|A1_TABELA|C|3|0|Tabela Preco|Tabela de preco padrao||`Vazio().Or.ExistCpo("DA0")` ||DA0|N|||||
84|A1_INCISS|C|1|0|ISS no Preco|ISS incluso no preço|`@!` ||||N|||S=Sim;N=Nao||
85|A1_SALDUPM|N|16|2|Sld.Moed.For|Saldo em Moeda Forte|`@E 9,999,999,999,999.99` ||||N|V||||
86|A1_PAGATR|N|16|2|Pag. Atras.|Pag. feitos com atraso|`@E 9,999,999,999,999.99` ||||N|V||||
87|A1_CXPOSTA|C|20|0|Caixa Postal|Caixa Postal|`@!` ||||N|||||
88|A1_ATIVIDA|C|7|0|C. Atividade|Codigo da Atividade|`@!` ||||N|||||
89|A1_CARGO1|C|15|0|Cargo 1|Cargo do Contato Coml.|`@!` |||||||||
90|A1_CARGO2|C|15|0|Cargo 2|Cargo do Contato CPD|`@!` |||||||||
91|A1_CARGO3|C|15|0|Cargo 3|Cargo do Contato C.Rec.|`@!` |||||||||
92|A1_ALIQIR|N|5|2|Aliq. IRRF|Aliquota IRRF|`@E 99.99` ||0|||A||||
93|A1_RTEC|C|6|0|Repres.Tec.|Representante Tecnico|`@!` |||||||||
94|A1_SUPER|C|6|0|Franquia|Franquia Responsavel|`@!` |||||||||
95|A1_RG|C|15|0|RG|Cedula de Identidade|||||N|||||
96|A1_OBSERV|C|40|0|Observacao|Observacao para relatorio|`@!` ||||N|||||
97|A1_CALCSUF|C|1|0|Desc.p/Sufr.|Calcula Desc. p/ Suframa|`!` ||||N|||S=Sim;N=Nao;I=ICMS||
98|A1_DTNASC|D|8|0|Dt.Aber/Nasc|Data de Nasc. ou Abertura|||||N|||||
99|A1_SALPEDB|N|16|2|Sl.Pd.Bl.Cre|Saldo Pedido Bloq.Credito|`@E 9,999,999,999,999.99` ||||N|||||
A0|A1_CLIFAT|C|6|0|Cliente Fat.|Cliente a Faturar|`@!` |`vazio().or.existcpo("SA1")` ||CLI|N|||||
A1|A1_GRPTRIB|C|3|0|Grp.Clientes|Grupo de Clientes|`@!` ||||N|||||
A2|A1_BAIRROC|C|30|0|Bairro Cob|Bairro de cobranca||||||||||
A3|A1_CEPC|C|8|0|Cep de Cobr.|Cep de Cobranca|`@R 99999-999` |`A030Cep("C")` |||N|||||
A4|A1_MUNC|C|15|0|Mun. Cobr.|Municipio de Cobranca|`@!` ||||N|||||
A5|A1_ESTC|C|2|0|Uf de Cobr.|Uf de Cobranca|`@!` ||||N|||||
A6|A1_CEPE|C|8|0|Cep Entr|Cep de Entrega|`@R 99999-999` |`A030Cep("E")` |||N|||||
A7|A1_BAIRROE|C|20|0|Bairro Entr.|Bairro de Entrega|||||N|||||
A8|A1_MUNE|C|15|0|Mun. entr|Municipio de Entrega|`@!` ||||N|||||
A9|A1_ESTE|C|2|0|Uf Entr|Estado de Entrega|`@!` |`Vazio() .Or. ExistCpo('SX5','12'+M->A1_ESTE)` ||12|N|A||||
B0|A1_SATIV1|C|6|0|Segmento 1|Segmentacao de Ativid. 1|`999999` |`ExistCpo("SX5","T3"+M->A1_SATIV1)` ||T3|N|||||
B1|A1_DSATIV1|C|60|0|Descrição|Descrição Segmento 1|`@!` ||If(!INCLUI,Posicione("SX5",1,xFilial("SX5")+ "T3" + SA1->A1_SATIV1,"X5DESCRI()"),"")||N|V|V|||
B2|A1_SATIV2|C|6|0|Segmento 2|Segmentacao de Ativid. 2|`999999` |`ExistCpo("SX5","T3"+M->A1_SATIV2)` ||T3|N|||||
B3|A1_TPESSOA|C|2|0|Tipo Pessoa|Tipo de Pessoa|`@!` ||||N|A|R|CI=Comercio/Industria;PF=Pessoa Fisica;OS=Prestacäo de Servico;EP=Empresa Publica||
B4|A1_TPISSRS|C|2|0|Tipo de Escr|Tipo de Escrituração|`99` |`Pertence("01/02/03/04/05/07/08/09/10/11/12/14/15/16/17/18/19")` |||N|A|R|||
B5|A1_DSATIV2|C|60|0|Descrição|Descrição Segmento 2|`@!` ||If(!INCLUI,Posicione("SX5",1,xFilial("SX5")+ "T3" + SA1->A1_SATIV2,"X5DESCRI()"),"")||N|V|V|||
B6|A1_CODLOC|C|8|0|Cod. Local|Código da Localidade||`Vazio().OR.ExistCPO("SX5","AB"+SUBS(M->A1_CODLOC,5,4))` |||||R|||
B7|A1_CODPAIS|C|5|0|Pais Bacen.|Cód. país Banco Central|`@R 99999` |`ExistCpo("CCH")` ||CCH|N|A|R|||
B8|A1_SATIV3|C|6|0|Segmento 3|Segmentacao de Ativid. 3|`999999` |`ExistCpo("SX5","T3"+M->A1_SATIV3)` ||T3|N|||||
B9|A1_DSATIV3|C|60|0|Descrição|Descrição Segmento 3|`@!` ||If(!INCLUI,Posicione("SX5",1,xFilial("SX5")+ "T3" + SA1->A1_SATIV3,"X5DESCRI()"),"")||N|V|V|||
C0|A1_SATIV4|C|6|0|Segmento 4|Segmentacao de Ativid. 4|`999999` |`ExistCpo("SX5","T3"+M->A1_SATIV4)` ||T3|N|||||
C1|A1_DSATIV4|C|60|0|Descrição|Descrição Segmento 4|`@!` ||If(!INCLUI,Posicione("SX5",1,xFilial("SX5")+ "T3" + SA1->A1_SATIV4,"X5DESCRI()"),"")||N|V|V|||
C2|A1_SATIV5|C|6|0|Segmento 5|Segmentacao de Ativid. 5|`999999` |`ExistCpo("SX5","T3"+M->A1_SATIV5)` ||T3|N|||||
C3|A1_DSATIV5|C|60|0|Descrição|Descrição Segmento 5|`@!` ||If(!INCLUI,Posicione("SX5",1,xFilial("SX5")+ "T3" + SA1->A1_SATIV5,"X5DESCRI()"),"")||N|V|V|||
C4|A1_SATIV6|C|6|0|Segmento 6|Segmentacao de Ativid. 6|`999999` |`ExistCpo("SX5","T3"+M->A1_SATIV6)` ||T3|N|||||
C5|A1_DSATIV6|C|60|0|Descrição|Descrição Segmento 6|`@!` ||If(!INCLUI,Posicione("SX5",1,xFilial("SX5")+ "T3" + SA1->A1_SATIV6,"X5DESCRI()"),"")||N|V|V|||
C6|A1_SATIV7|C|6|0|Segmento 7|Segmentacao de Ativid. 7|`999999` |`ExistCpo("SX5","T3"+M->A1_SATIV7)` ||T3|N|||||
C7|A1_DSATIV7|C|60|0|Descrição|Descrição Segmento 7|`@!` ||If(!INCLUI,Posicione("SX5",1,xFilial("SX5")+ "T3" + SA1->A1_SATIV7,"X5DESCRI()"),"")||N|V|V|||
C8|A1_SATIV8|C|6|0|Segmento 8|Segmentacao de Ativid. 8|`999999` |`ExistCpo("SX5","T3"+M->A1_SATIV8) .And. TmkSeg("1")` ||T3|N|||||
C9|A1_DSATIV8|C|60|0|Descrição|Descrição Segmento 8|`@!` ||If(!INCLUI,Posicione("SX5",1,xFilial("SX5")+ "T3" + SA1->A1_SATIV8,"X5DESCRI()"),"")||N|V|V|||
D0|A1_CODMARC|C|6|0|Cod.Marcacao|Marcacao|`@!` ||||N|||||
D1|A1_CODAGE|C|3|0|Cód.Agente|Código do agente|`@!` |`ExistCPO("SY5")` ||SY5|N|||||
D2|A1_VM_MARC|M|20|0|Marcacao|Cod.Marcação|||E_MSMM(M->A1_CODMARC,20)||N||V|||
D3|A1_COMAGE|N|15|8|% Comissão|% Comissão agente|`@E 999,999.99999999` |`Positivo().AND.M->A1_COMAGE<=100` |||N|||||
D4|A1_TIPCLI|C|1|0|Tipo Cliente|Tipo Cliente Exportação|`@!` ||"1"||N|||1=Importador;2=Consignee;3=Notify;4=Todos||
D5|A1_DEST_1|C|3|0|Destino 1|Destino 1|`@!` |`EECFBDEST(M->A1_DEST_1,"1")` ||YR1|N|||||
D6|A1_EMAIL|C|30|0|E-Mail|E-Mail|||||N|||||
D7|A1_DEST_2|C|3|0|Destino 2|Destino 2|`@!` |`EECFBDEST(M->A1_DEST_2,"2")` ||YR1|N|||||
D8|A1_CODMUN|C|5|0|Cod. Mun. ZF|Cod. Mun. ZF Manaus e ALC||`Vazio() .Or. ExistCpo("SX5","S1"+M->A1_CODMUN)` ||S1|N|||||
D9|A1_DEST_3|C|3|0|Destino 3|Destino 3|`@!` |`EECFBDEST(M->A1_DEST_3,"3")` ||YR1|N|||||
E0|A1_HPAGE|C|30|0|Home-Page|Home-Page|||||N|||||
E1|A1_CBO|C|7|0|Cod. CBO|Codigo do CBO|`@!` ||||N|A|R||`M->A1_PESSOA = "F"` |
E2|A1_CNAE|C|9|0|Cod CNAE|Código CNAE do Cliente|`9999-9/99` |`Vazio() .OR. ExistCpo('CC3')` ||CC3|N|A|R|||
E3|A1_CONDPAG|C|5|0|Cond. Pagto|Cond. Pagto|`@!` |`Vazio().Or.ExistCpo("SY6",M->A1_CONDPAG,1)` ||SY6|N|||||
E4|A1_DIASPAG|N|3|0|Dias  Pagto|Dias  Pagto|`999` |`Vazio() .Or. ExistCpo("SY6",M->A1_CONDPAG+Str(M->A1_DIASPAG,AVSX3("A1_DIASPAG",3)),1)` |||N|||||
E5|A1_DESCPAG|C|60|0|Descrição|Descricao em Portugues|||E_FIELD2(SA1->A1_CONDPAG+STR(SA1->A1_DIASPAG,3),"SY6",1,,"SY6->Y6_DESC_P",60)||N|V|V|||
E6|A1_OBS|C|6|0|Observacoes|Observacoes|`@!` ||||N|||||
E7|A1_AGREG|C|4|0|Agre. liber.|Agregador de liberacao|`@!` ||||N|||||
E8|A1_VM_OBS|M|60|0|Observacoes|Observações|||E_MSMM(SA1->A1_OBS,60)||N||V|||
E9|A1_CODHIST|C|6|0|Cod.Historic|Codigo da Obs. do Hist.|`999999` |||||A||||
F0|A1_RECINSS|C|1|0|Rec. INSS|Recolhe INSS <S/N> ?|`@!` |`pertence("SN")` |||N|||S=Sim;N=Nao||
F1|A1_RECCOFI|C|1|0|Rec.COFINS|Recolhe COFINS  ?|`@!` |`pertence("SNP")` |"N"||N|||S=Sim;N=Nao;P=Empresa Pública||
F2|A1_RECCSLL|C|1|0|Rec. CSLL|Recolhe CSLL ?|`@!` |`pertence("SNP")` |"N"||N|||S=Sim;N=Nao;P=Empresa Pública||
F3|A1_RECPIS|C|1|0|Rec. PIS|Recolhe PIS ?|`@!` |`pertence("SNP")` |"N"||N|||S=Sim;N=Nao;P=Empresa Pública||
F4|A1_HISTMK|M|35|0|Hist. Atend.|Historico do Atendimento|`@!` ||||N|A|V|||
F5|A1_TIPPER|C|2|0|Tipo Periodo|Tipo de Periodo|`@!` |`Vazio() .or. Pertence("02/03/04/05/06/10/15/30")` |||N|||02=Toda segunda;03=Toda terca;04=Toda quarta;05=Toda quinta;06=Toda sexta;10=a cada 10 dias;15=a cada 15 dias;30=todo fim de mes||
F6|A1_SALFIN|N|16|2|Saldo LC Sec|Saldo LC secundario|`@E 9,999,999,999,999.99` ||||N|V||||
F7|A1_SALFINM|N|16|2|Sld LC SE MF|Saldo LC Secundario na MF|`@E 9,999,999,999,999.99` ||||N|V||||
F8|A1_CONTAB|C|15|0|C.Contab.Imp|Conta contabil importacäo|`@!` ||||N|||||
F9|A1_B2B|C|1|0|Utiliza B2B|Utiliza B2B?|`@!` |`Pertence("12")` |"2"||N|||1=Sim;2=Nao||
G0|A1_GRPVEN|C|6|0|Grp.Vendas|Grupo de Vendas.|`@!` |`Vazio() .or. ExistCpo("ACY")` ||ACY||||||
G1|A1_MSBLQL|C|1|0|Status|Status do Registro|`@!` |`pertence("12")` |"2"|||||1=Inativo;2=Ativo||
G2|A1_INSCRUR|C|18|0|Insc.Rural|Inscricao produtor rural|`@!` |||||||||
G3|A1_CLICNV|C|1|0|Cli Convenio|O Cliente e¦ Convenio?||`Pertence("01")` ||||||0=Nao;1=Sim||
G4|A1_COMPLEM|C|50|0|Complemento|Complemento do endereço|`@!` ||||N|A||||
G5|A1_HRCAD|C|5|0|Hr.Cadastro|Hora de Cadastro|`99:99` ||SUBSTR(TIME(),1,5)|||V|R|||
G6|A1_DTCAD|D|8|0|Dt.Cadastro|Data de Cadastro|||DDATABASE|||V|R|||
G7|A1_CLIPRI|C|6|0|Cli. Primar.|Cliente Primário|`@!` |`VAZIO() .OR. ExistCpo("SA1")` ||SA1||A|R|||
G8|A1_LOJPRI|C|2|0|Loja Cli.Pri|Loja do Cliente Primário|`@!` |||||V|R|||
G9|A1_CODSEG|C|6|0|Cod.Segmento|Código do Segmento|`@!` |`VAZIO() .OR. (ExistCpo('AOV',M->A1_CODSEG)    .And. CRMA620VLD(M->A1_CODSEG))` ||AOVP|N|A|R|||
H0|A1_DESSEG|C|40|0|Descrição|Descrição do Segmento|`@!` ||if(!Inclui,Posicione("AOV",1,XFILIAL("AOV")+SA1->A1_CODSEG,"AOV_DESSEG"),"")||N|V|V|||
H1|A1_NUMRA|C|15|0|Numero RA|Numero da RA aluno|`@!` |||||||||
H2|A1_SITUA|C|2|0|Situacão FRT|Situacão Front Loja|||||N|||||
H3|A1_SUBCOD|C|1|0|Sub Codigo|Sub codigo||||||||||
H4|A1_CDRDES|C|6|0|Reg. Cliente|Regiao do Cliente|`@!` |`ExistCpo("DUY",M->A1_CDRDES,1)` ||DUY|N|||||
H5|A1_REGDES|C|30|0|Des.Reg.Cli.|Descr. Regiao do Cliente|`@!` ||IIF(Inclui,'',Posicione('DUY',1,xFilial('SA1')+SA1->A1_CDRDES,'DUY_DESCRI'))|||V|V|||
H6|A1_FILDEB|C|2|0|Fil.Debito|Filial de Debito||`Vazio() .Or. TMSValidEmp(cEmpAnt+M->A1_FILDEB)` ||DLB||||||
H7|A1_CODFOR|C|15|0|Cod.Fornec.|Cod.Fornec.para o cliente||||||||||
H8|A1_ABICS|C|4|0|Cod. Abics|Cod. Abics|`9999` ||||N|||||
H9|A1_BLEMAIL|C|1|0|Boleto Email|Boleto Via Email (Cnab)|`@!` |||||||1=Sim;2=Nao||
I0|A1_TIPOCLI|C|2|0|Tipo Cliente|Tipo do Cliente|`@!` |`FG_STRZERO("M->A1_TIPOCLI",2).and. naovazio() .and. EXISTCPO("SX5","TC"+M->A1_TIPOCLI)` ||TC||||||
I1|A1_VINCULO|C|2|0|P. Vinculo|Pessoa Vinculada|`@!` |`ExistCpo("CC1")` ||CC1TIP|N|A|R|||
I2|A1_DTINIV|D|8|0|Dt Ini Vincu|Data Inicial do Vinculo|||||N|A|R|||
I3|A1_DTFIMV|D|8|0|Dt Fim Vincu|Data Final do Vinculo|||||N|A|R|||
I4|A1_LOCCONS|C|2|0|Armazem Dest|Armazem Destino|`@!` |`ExistCpo("NNR")` ||NNR|N|||||
I5|A1_CODMUNE|C|5|0|Cd Mun Entre|Municipio da Entrega|`@9` |`Vazio() .Or. ExistCpo("CC2",M->A1_ESTE+M->A1_CODMUNE)` ||CC2ENT||||||
I6|A1_PERFIL|N|2|0|Nota Perfil|Nota Perfil do Cliente|`99` |||||A|R|||
I7|A1_HRTRANS|C|5|0|Translado|Translado|`99:99` |`Vazio() .OR. AtVldHora(M->A1_HRTRANS,.T.)` ||||A|R|||
I8|A1_UNIDVEN|C|6|0|Un. Venda|Unidade de Venda|`@!` |`ExistCpo('ADK')` ||ADK||A|R|||
I9|A1_TIPPRFL|C|1|0|Tipo Perfil|Tipo de Perfil do cliente|||||N|A|R|1=Perfil 1;2=Perfil 2;3=Perfil 3;4=Perfil 4;5=Perfil 5;6=Perfil 6||
J0|A1_PRF_VLD|D|8|0|Data Perfil|Data de validade do Perfi|||||N|A|R|||
J1|A1_PRF_COD|C|6|0|Memo Perfil|Codigo do campo memo de P|||||N|V|R|||
J2|A1_PRF_OBS|M|10|0|Obs. Perfil|Observacao do Perfil|||||N|A|R|||
J3|A1_REGPB|C|1|0|Reg.Paraíba|Regime Paraíba|`@!` |`Pertence(" 12" )` |||S|A|R|1=Sim;2=Não||
J4|A1_TPREG|C|1|0|Tp. Reg|Tipo de Regime|`@!` |`Pertence(" 12")` |||N|A|R|1=Não Cumulativo;2=Cumulativo||
J5|A1_USADDA|C|1|0|Usa DDA|Cliente aderiu ao DDA|`@!` |`Pertence("12")` |"2"||N|A|R|1=Sim;2=Nao||
J6|A1_SIMPLES|C|1|0|Opt. Simples|Clie. optante SIMPLES/SC|`@!` ||||N|||1=Sim;2=Não||
J7|A1_RESERVE|C|1|0|Reserve|Situação no Reserve|`@!` ||"1"||N|V|R|1=Pendente inclusão;2=Pendente alteração;3=Pendente exclusão;4=Sincronizado||
J8|A1_REGESIM|C|1|0|Rg. Simp. MT|Reg. Simlificado MT|`@!` ||"2"||N|A|R|1=Sim;2=Não||
J9|A1_ORIGEM|C|2|0|Orig.Cliente|Origem do Cliente|`@!` ||||N|V|R|||
K0|A1_PERCATM|N|5|2|P. Carga Med|Pecentual de Carga Media|`@E 99.99` ||||N|A|R|||
K1|A1_IPWEB|C|20|0|IP WebSite|IP WebSite do Cliente|`@!` |||||||||
K2|A1_IRBAX|C|1|0|IRPJ baixa|IRPJ baixa|`@!` |`Pertence("12")` |"2"||N|A|R|1=Sim;2=Não||
K3|A1_INDRET|C|2|0|Ind. Ret.|Indicador de Retencao|`@!` |`Vazio() .Or. ExistCpo('FR0','001'+M->A1_INDRET)` ||FR0001||||||
K4|A1_NIF|C|40|0|Código NIF|Num. de Ident. Fiscal|`@9` ||||N|A|R|||
K5|A1_MSEXP|C|8|0|Ident.Exp.|Ident.Exp.Dados|||||N|V|R|||
K6|A1_IDHIST|C|20|0|Id.Historico|Id.Historico|`@!` ||Iif(FindFunction("IdHistFis"), IdHistFis(),"")||N||R|||
K7|A1_FRETISS|C|1|0|F.Ret.ISS|Forma de retenção do ISS|`@!` |`Pertence(' 12')` |||N|A|R|1=Cons Vlr Mínimo;2=Sempre Retém||
K8|A1_ENDNOT|C|1|0|End.Not.Form|Endereço não formatado|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
K9|A1_CTARE|C|1|0|Contr TARE ?|Contribuinte TARE ?|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Nao||
L0|A1_CODSIAF|C|4|0|Cod.Mun.SIAF|Cod.Municipio SIAFI|`@!` |||CC2SIA|N|||||
L1|A1_CEINSS|C|14|0|Cad Esp INSS|Cadastro Especifico INSS|`@!` |||||A|R|||
L2|A1_ABATIMP|C|1|0|Modo Abat Im|Modo Abatim. Imposto|||"1"||N|A|R|1=Calculo do Sistema;2=Efetua Retencao;3=Nao efetua retencao||
L3|A1_ALIFIXA|C|1|0|Alíq. Fixa|Ind. Alíquota fixa|`@!` |`Pertence('12')` |||N|A|R|1=Sim;2=Não||
L4|A1_CHVCAM|C|14|0|Código|Código da Campanha|`@!` ||||N|V|R|||
L5|A1_CODTER|C|6|0|Cod. Terr.|Código do Território|`@!` |`Vazio() .Or. ExistCpo("AOY")` |||N|V|R|||
L6|A1_CODMEMB|C|14|0|Membro|Código do Membro|`@!` ||||N|V|R|||
L7|A1_CODFID|C|40|0|Cod. Fidelid|Código Cartão Fidelidade|`@!` ||||N|A|R|||
L8|A1_CONTRIB|C|1|0|Contribuinte|Contribuinte do ICMS|`@!` |`Pertence(' 12')` |||N|A|R|1=Sim;2=Não||
L9|A1_CRDMA|C|1|0|Cr.Est.Ma|Crédito Estimulo Manaus|`@!` |`Pertence(" 123")` |||N|A|R|1=Nao Incent.;2=Construtora;3=Outros||
M0|A1_DESCAM|C|40|0|Desc. Camp.|Descrição da Campanha|`@!` ||IIF(!EMPTY(M->A1_CHVCAM),POSICIONE("SUO",1, XFILIAL("SUO")+M->A1_CHVCAM,"UO_DESC"),"")||N|V|V|||
M1|A1_DSCMEMB|C|100|0|Desc. Membro|Descrição do Membro|`@!` ||IIF(!INCLUI,CRMA640Gat(M->A1_TPMEMB,M->A1_CODMEMB),"")||N|V|V|||
M2|A1_ENTID|C|2|0|Tp.Entidade|Tipo de Entidade|`99` |`Pertence(" 00/01/02/03/04/05/06/07/08/09/10")` |||N|A|R|00=PJ D Pv;01=Órg,A Fd;02=Aq Ap;03=EP/SocEcMta/PJ;04=//PJ-Tr P;05=//-Sv Pr F;06=//-Dm Sv;07=//-D E;08=//-A Pf;09=//-Cb;10=Pg n E||
M3|A1_ENTORI|C|6|0|Ent. Origem|Entidade de Origem|`@!` |`If(FindFunction("A030VldCd"),A030VldCd() ,.T.)` ||F3ORIG|N|A|R||`If(FindFunction("A030VldEnt"),A030VldEnt(),.T.)` |
M4|A1_FILTRF|C|2|0|Fil. Transf.|Filial para transferência||`Vazio() .Or. MtValidFil(cEmpAnt+M->A1_FILTRF)` ||DLB|N|A|R|||
M5|A1_FOMEZER|C|1|0|Fome Zero|Participação Fome Zero|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
M6|A1_IENCONT|C|1|0|Destaca IE|Destaca IE não Contr.|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Nao||
M7|A1_IMGUMOV|C|100|0|URL.Img.uMov|Ver imagem uMov.me|`@!` ||||N|V|R|||
M8|A1_IDESTN|C|30|0|Id.Estr.Neg|Id. de Acesso Estr. Neg.|`@!` ||IIF(FINDFUNCTION("CRMXNVLEST"),CRMXNVLEST(M->A1_VEND)[1],"")||N|V|R|||
M9|A1_HREXPO|C|8|0|Hr. Exporta|Hora da ultima Exportação||||||V|R|||
N0|A1_MINIRF|C|1|0|Vlr. Min. IR|Valor Mínimo de IRRF|`@!` |`Pertence ("12")` |"2"||N|A|R|1=Sim;2=Nao||
N1|A1_NOMTER|C|40|0|Nome Territ.|Nome do Território|`@!` ||IIF(!INCLUI,ALLTRIM(POSICIONE("AOY",1,XFILIAL("AOY")+SA1->A1_CODTER,"AOY_NMTER")),"")||N|V|V|||
N2|A1_NVESTN|N|2|0|Nvl. Est.Neg|Nvl de Acesso a Estr. Neg|`99` ||IIF(FINDFUNCTION("CRMXNVLEST"),CRMXNVLEST(M->A1_VEND)[2],0)||N|V|R|||
N3|A1_INOVAUT|C|1|0|Inovar Auto|Inovar Auto|`@!` |`Pertence(' 12')` |||N|A|R|1=Sim;2=Não||
N4|A1_INCLTMG|C|1|0|Inc.Prd.Leit|Incentivo Prod.Leite MG|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
N5|A1_INCULT|C|1|0|Inc. Cultura|Incentivo a Cultura|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
N6|A1_ISSRSLC|C|1|0|LC ISS RS|LC Enq. ISS|`@!` |`Pertence ("12")` |||N|A|R|||
N7|A1_MATFUN|C|6|0|Matricula|Matricula do usuário|`@!` |`Vazio() .OR. ExistCpo("SRA")` ||SRA|N|A|R||`M->A1_CLIFUN="1"` |
N8|A1_PERFECP|N|5|2|P.Carga Fecp|Per.Carga devida ao Fundo|`@E 99.99` ||||N|A|R|||
N9|A1_ORIGCT|C|1|0|Orig. Conta|Origem do Cliente|`@!` |`Vazio() .OR. Pertence("123456789AB")` |||N|A|R|1=Mailing;2=Campanha;3=Web;4=Indicação;5=Evento;6=Anúncio;7=Parceiro;8=Relações públicas;9=Seminário;A=Boca-a-boca;B=Outros||
O0|A1_OUTRMUN|C|10|0|Outros Mun.|Cod. Outros Municipios|||||N|A|R|||
O1|A1_RESFAT|C|1|0|Fat. Viagem|Forma Faturamento Viagem|`9` |`Pertence('12')` |||N|A|R|1=Nota Normal;2=Nota Debito||
O2|A1_RFABOV|C|1|0|Rec. FABOV|Recolhe FABOV|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Nao||
O3|A1_RFACS|C|1|0|Rec. FACS|Recolhe FACS|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Nao||
O4|A1_RFASEMT|C|1|0|Rec.FASE-MT|Recolhe FASE-MT|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
O5|A1_PRSTSER|C|1|0|Ind. Prest.|Ind. Prestador de Serv.|`@!` ||||N|A|R|||
O6|A1_RECFET|C|1|0|Rec. FETHAB|Recolhe FETHAB|`@!` |`Pertence("12")` |||||R|1=Sim;2=Não||
O7|A1_RECFMD|C|1|0|Rec.FAMAD|Recolhe FAMAD|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
O8|A1_SIMPNAC|C|1|0|Opt Simp Nac|Optante Simples Nacional|`@!` |`Pertence(" 12")` |||N|||1=Sim;2=Não||
O9|A1_RECIRRF|C|1|0|Recolhe IRRF|Cliente recolhera IRRF|`@!` |`Pertence("12 ")` |||N|A|R|1=Sim;2=Nao||
P0|A1_RIMAMT|C|1|0|Rec. IMA-MT|Recolhe IMA-MT|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
P1|A1_TDA|C|1|0|TDA|Taxa Dif. Acesso|`@!` ||||N|A|R|1=Sim;2=Não||
P2|A1_TIMEKEE|C|8|0|Timekeeper|Advogado apontador Horas|`@!` |||FSA|N|A|R|||
P3|A1_USERLGA|C|17|0|Log de Alter|Log de Alteração|||||N|V|R|||
P4|A1_USERLGI|C|17|0|Log de Inclu|Log de Inclusão|||||N|V|R|||
P5|A1_TPJ|C|1|0|TPJ|Tipo de Pessoa Jurídica|`@!` |`Pertence(" 1234")` |||N|||1=ME - Micro Empresa;2=EPP - Empresas de Pequeno Porte;3=MEI - Microempreendedor Individual;4=Não Optante||
P6|A1_TPMEMB|C|1|0|Tipo Membro|Tipo do Membro|`@!` |||||V|R|1=Unidade de Negócio;2=Papeis do Usuario;3=Equipe||
P7|A1_TPNFSE|C|2|0|T.P NFSE|Tipo de pessoa NFSE|`@!` |`Pertence(" 012345")` |||N|A|R|0=Outro;1=SUS;2=Executivo;3=Bancos;4=Comercio/Industria;5=Legislativo/Judiciario||
P8|A1_TPCAMP|C|1|0|Tipo Camp|Tipo de Campanha|`@!` ||||N|V|R|||
P9|A1_TPDP|C|1|0|Calc. TPDP|Calcula TPDP|`@!` |`Pertence(" 12")` |"2"||N|A|R|1=Sim;2=Nao||


## SIX - Índices da tabela

ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|A1_FILIAL+A1_COD+A1_LOJA|Codigo + Loja|||S|
2|A1_FILIAL+A1_NOME+A1_LOJA|Nome + Loja|||S|
3|A1_FILIAL+A1_CGC|CNPJ/CPF|||S|
4|A1_FILIAL+A1_TEL+A1_DDD+A1_DDI|Telefone + DDD + DDI|||S|
5|A1_FILIAL+A1_NREDUZ|N Fantasia|||S|
6|A1_FILIAL+A1_GRPVEN|Grp.Vendas|ACY||S|
7|A1_FILIAL+A1_NUMRA|Numero RA|||S|
8|A1_FILIAL+A1_VINCULO|P. Vinculo|CC1||S|
9|A1_FILIAL+A1_IDHIST|Id.Historico|||S|
A|A1_FILIAL+A1_VEND+A1_COD+A1_LOJA|Vendedor + Codigo + Loja|||S|
B|A1_FILIAL+A1_CLIPRI+A1_LOJPRI+A1_COD+A1_LOJA|Cli. Primar. + Loja Cli.Pri + Codigo + Loja|||S|
C|A1_FILIAL+A1_SITUA|Situacão FRT|||S|
D|A1_FILIAL+A1_CONTA|C. Contabil|||S|


