# SF2 - Cabeçalho das NF de Saída
## SX3 - Campos da tabela

X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|F2_DOC|C|9|0|Numero|Numero do Docto. de Saida|`@!` |`ExistChav("SF2")` |||S|||||
02|F2_SERIE|C|3|0|Serie Docto.|Serie do Documento|`!!!` ||||S|||||
03|F2_CLIENTE|C|6|0|Cliente|Codigo do Cliente|`@!` |||SA1|S|||||
04|F2_LOJA|C|2|0|Loja|Loja do Cliente|`@!` |`Iif(cPaisLoc == "BRA" ,.T.,  Vazio() .or. VldF2Loj())` |||S|||||
05|F2_COND|C|3|0|Cond. Pagto|Codigo da condic. de pgto|`@!` |`existcpo("SE4")` ||SE4|S|||||
06|F2_DUPL|C|9|0|Num. Titulo|Numero do titulo|`@!` ||||N|||||
07|F2_EMISSAO|D|8|0|DT Emissao|Data de Emissao da NF|||ddatabase||N|||||
08|F2_EST|C|2|0|Estado|Estado Destino do Materia|`@!` |`ExistCpo("SX5","12"+M->F2_EST).And.MaFisRef("NF_UFDEST","MT100",M->F2_UF)` |||N|||||
09|F2_FRETE|N|14|2|Vlr.Frete|Valor do Frete|`@E 999,999,999.99` |`MaFisRef("NF_FRETE","MT100",M->F2_FRETE)` |||N|||||
10|F2_SEGURO|N|14|2|Vlr.Seguro|Valor do Seguro|`@E 999,999,999.99` |`MaFisRef("NF_SEGURO","MT100",M->F2_SEGURO)` |||N|||||
11|F2_ICMFRET|N|14|2|ICMS Frete|Valor do Frete / Seguro|`@E 999,999,999.99` |`MaFisRef("NF_ICMFRETE","MT100",M->F2_ICMFRET)` |||N|||||
12|F2_TIPOCLI|C|1|0|Tipo Consumi|Tipo de Consumidor|`@!` ||||N|||||
13|F2_VALBRUT|N|14|2|Vlr.Bruto|Valor Bruto da NF|`@E 99,999,999,999.99` |`MaFisRef("NF_TOTAL","MT100",M->F2_VALBRUT)` |||N|||||
14|F2_VALICM|N|14|2|Vlr.ICMS|Valor do ICMS|`@E 999,999,999.99` |`MaFisRef("NF_VALICM","MT100",M->F2_VALICM)` |||N|||||
15|F2_BASEICM|N|14|2|Base p/ICMS|Base de Calculo para ICM|`@E 999,999,999.99` |`MaFisRef("NF_BASEICM","MT100",M->F2_BASEICM)` |||N|||||
16|F2_VALIPI|N|14|2|Vlr.IPI|Valor do IPI|`@E 999,999,999.99` |`MaFisRef("NF_VALIPI","MT100",M->F2_VALIPI)` |||N|||||
17|F2_BASEIPI|N|14|2|Base p/IPI|Base de calculo para IPI|`@E 999,999,999.99` |`MaFisRef("NF_BASEIPI","MT100",M->F2_BASEIPI)` |||N|||||
18|F2_VALMERC|N|14|2|Vlr.Mercad|Valor da Mercadoria|`@E 999,999,999.99` ||||N|||||
19|F2_NFORI|C|9|0|Docto. Orig.|Docto. Orig. Qdo Devoluca|`@!` ||||N|||||
20|F2_DESCONT|N|14|2|Descontos|Descontos da Nota Fiscal|`@E 999,999,999.99` |`MaFisRef("NF_DESCONTO","MT100",M->F2_DESCONT)` |||N|||||
21|F2_SERIORI|C|3|0|Sér.Original|Série Orig. Qdo Devolucao|`!!!` ||||N|||||
22|F2_TIPO|C|1|0|Tipo da nota|Nota Venda/Devolucao|`@!` |`Pertence("NCPIDB")` |||N|||||
23|F2_ESPECI1|C|10|0|Especie 1|Especie 1|`@!` ||||N|||||
24|F2_ESPECI2|C|10|0|Especie 2|Especie 2|`@!` ||||N|||||
25|F2_ESPECI3|C|10|0|Especie 3|Especie 3|`@!` ||||N|||||
26|F2_ESPECI4|C|10|0|Especie 4|Especie 4|`@!` ||||N|||||
27|F2_VOLUME1|N|6|0|Volume 1|Volume 1|`999999` ||||N|||||
28|F2_VOLUME2|N|6|0|Volume 2|Volume 2|`999999` ||||N|||||
29|F2_VOLUME3|N|6|0|Volume 3|Volume 3|`999999` ||||N|||||
30|F2_VOLUME4|N|6|0|Volume 4|Volume 4|`999999` ||||N|||||
31|F2_ICMSRET|N|14|2|ICMS Retido|ICMS Retido na Fonte|`@E 999,999,999.99` |`MaFisRef("NF_VALSOL","MT100",M->F2_ICMSRET)` |||N|||||
32|F2_PLIQUI|N|11|4|Peso Liquido|Peso Liquido da N.F.|`@E 999999.9999` ||||N|||||
33|F2_PBRUTO|N|11|4|Peso Bruto|Peso Bruto da N.F.|`@E 999999.9999` ||||N|||||
34|F2_TRANSP|C|6|0|Transp.|Codigo da Transportadora|`@!` |||SA4|N|||||
35|F2_REDESP|C|6|0|Redespacho|Transp. para Redespacho|`@!` |||SA4|N|||||
36|F2_VEND1|C|6|0|Vendedor 1|Vendedor 1|`@!` |`Vazio() .or. ExistCpo("SA3",M->F2_VEND1)` ||SA3|N|||||
37|F2_VEND2|C|6|0|Vendedor 2|Vendedor 2|`@!` |`Vazio() .or. ExistCpo("SA3",M->F2_VEND2)` ||SA3|N|||||
38|F2_VEND3|C|6|0|Vendedor 3|Vendedor 3|`@!` |`Vazio() .or. ExistCpo("SA3",M->F2_VEND3)` ||SA3|N|||||
39|F2_VEND4|C|6|0|Vendedor 4|Vendedor 4|`@!` |`Vazio() .or. ExistCpo("SA3",M->F2_VEND4)` ||SA3|N|||||
40|F2_VEND5|C|6|0|Vendedor 5|Vendedor 5|`@!` |`Vazio() .or. ExistCpo("SA3",M->F2_VEND5)` ||SA3|N|||||
41|F2_OK|C|4|0|Nota a Impr.|Inform. de Nota a Imprim.|||||N|||||
42|F2_FIMP|C|1|0|Flag de Imp.|Flag de Impressao|||||N|||||
43|F2_DTLANC|D|8|0|Dt. do Lanc.|Data do Lanc. Contab.|||ddatabase||N|||||
44|F2_DTREAJ|D|8|0|Dt. Reajuste|Data do Reajuste|||ddatabase||N|||||
45|F2_REAJUST|C|3|0|Cod.Reajuste|Cod. do Reajuste|||||N|||||
46|F2_DTBASE0|D|8|0|Data Base 0|Data Base 0 do Reajuste|||||N|||||
47|F2_FATORB0|N|14|4|Fator Base 0|Fator na Data Base 0|`@E 999,999,999.9999` ||||N|||||
48|F2_DTBASE1|D|8|0|Data Base 1|Data Base 1 do Reajuste|||||N|||||
49|F2_FATORB1|N|14|4|Fator Base 1|Fator na Data Base 1|`@E 999,999,999.9999` ||||N|||||
50|F2_VARIAC|N|10|4|Variacao|Variacao|`@E 99,999.9999` ||||N|||||
51|F2_FILIAL|C|2|0|Filial|Filial do Sistema|||||N|||||
52|F2_BASEISS|N|14|2|Base ISS|Valor Base do ISS|`@E 99,999,999,999.99` |`MaFisRef("NF_BASEISS","MT100",M->F2_BASEISS)` |||N|||||
53|F2_VALISS|N|14|2|Valor ISS|Valor do ISS|`@E 99,999,999,999.99` |`MaFisRef("NF_VALISS","MT100",M->F2_VALISS)` |||N|||||
54|F2_VALFAT|N|16|2|Valor Fatura|Valor Faturado|`@E 99,999,999,999.99` ||||N|||||
55|F2_CONTSOC|N|14|2|Vl.Contr.Soc|Valor Contr.Seg.Social|`@E 999,999,999.99` |`MaFisRef("NF_FUNRURAL","MT100",M->F2_CONTSOC)` |||N|||||
56|F2_BRICMS|N|14|2|Base ICM Sol|Base ICMS Solidario|`@E 999,999,999.99` |`MaFisRef("NF_BASESOL","MT100",M->F2_BRICMS)` |||N|||||
57|F2_FRETAUT|N|14|2|Vl.Frete Aut|Valor do Frete Autonomo|`@E 999,999,999.99` |`MaFisRef("NF_AUTONOMO","MT100",M->F2_FRETAUT)` |||N|||||
58|F2_ICMAUTO|N|14|2|Vl.Icm Frete|Valor do ICMs Frete|`@E 999,999,999.99` |`MaFisRef("NF_VALICA","MT100",M->F2_ICMAUTO)` |||N|||||
59|F2_DESPESA|N|14|2|Vl. Despesa|Valor da Despesa Acessor.|`@E 999,999,999.99` |`MaFisRef("NF_DESPESA","MT100",M->F2_DESPESA)` |||N|||||
60|F2_NEXTDOC|C|9|0|Prox Nota|Proxima Nota Fiscal|`@!` ||||N|||||
61|F2_NEXTSER|C|3|0|Prox. Serie|Proxima Serie|`!!!` ||||N|||||
62|F2_ESPECIE|C|5|0|Espec.Docum.|Espécie do Documento|`@!` |`Vazio().or.ExistCpo("SX5","42"+M->F2_ESPECIE)` ||42|N|||||
63|F2_PDV|C|10|0|Numero PDV|Numero do PDV|`@!` ||||N|V||||
64|F2_MAPA|C|10|0|Numero MAPA|Numero MAPA|`@!` ||||N|V||||
65|F2_ECF|C|1|0|Serie ECF|Serie ECF ou nao.|`@!` ||||N|||||
66|F2_PREFIXO|C|3|0|Prefixo|Prefixo do Titulo Gerado|`@!` ||||N|V||||
67|F2_BASIMP1|N|14|2|Base Imp. 1|Base de Calculo Imposto 1|`@E  99,999,999,999.99` |`MaFisRef("NF_BASEIV1","MT100",M->F2_BASIMP1)` |||N|||||
68|F2_BASIMP2|N|14|2|Base Imp. 2|Base de Calculo Imposto 2|`@E  99,999,999,999.99` |`MaFisRef("NF_BASEIV2","MT100",M->F2_BASIMP2)` |||N|||||
69|F2_BASIMP3|N|14|2|Base Imp. 3|Base de Calculo Imposto 3|`@E  99,999,999,999.99` |`MaFisRef("NF_BASEIV3","MT100",M->F2_BASIMP3)` |||N|||||
70|F2_BASIMP4|N|14|2|Base Imp. 4|Base de Calculo Imposto 4|`@E  99,999,999,999.99` |`MaFisRef("NF_BASEIV4","MT100",M->F2_BASIMP4)` |||N|||||
71|F2_BASIMP5|N|14|2|Base Imp. 5|Base de Calculo Imposto 5|`@E  99,999,999,999.99` |`MaFisRef("NF_BASECF2","MT100",M->F2_BASIMP5)` |||N|||||
72|F2_BASIMP6|N|14|2|Base Imp. 6|Base de Calculo Imposto 6|`@E  99,999,999,999.99` |`MaFisRef("NF_BASEPS2","MT100",M->F2_BASIMP6)` |||N|||||
73|F2_VALIMP1|N|14|2|Valor Imp. 1|Valor do Imposto 1|`@E  99,999,999,999.99` |`MaFisRef("NF_VALIV1","MT100",M->F2_VALIMP1)` |||N|||||
74|F2_VALIMP2|N|14|2|Valor Imp. 2|Valor do Imposto 2|`@E  99,999,999,999.99` |`MaFisRef("NF_VALIV2","MT100",M->F2_VALIMP2)` |||N|||||
75|F2_VALIMP3|N|14|2|Valor Imp. 3|Valor do Imposto 3|`@E  99,999,999,999.99` |`MaFisRef("NF_VALIV3","MT100",M->F2_VALIMP3)` |||N|||||
76|F2_VALIMP4|N|14|2|Valor Imp. 4|Valor do Imposto 4|`@E  99,999,999,999.99` |`MaFisRef("NF_VALIV4","MT100",M->F2_VALIMP4)` |||N|||||
77|F2_VALIMP5|N|14|2|Valor Imp. 5|Valor do Imposto 5|`@E  99,999,999,999.99` |`MaFisRef("NF_VALCF2","MT100",M->F2_VALIMP5)` |||N|||||
78|F2_VALIMP6|N|14|2|Valor Imp. 6|Valor do Imposto 6|`@E  99,999,999,999.99` |`MaFisRef("NF_VALPS2","MT100",M->F2_VALIMP6)` |||N|||||
79|F2_ORDPAGO|C|6|0|Ordem Pagto|Ordem de Pagamento||||||||||
80|F2_NFCUPOM|C|12|0|NF de Cupom|NF referente Cupom Fiscal|`@!` |||||||||
81|F2_VALINSS|N|14|2|Valor INSS|Valor INSS|`@E 999,999,999.99` |`MaFisRef("NF_VALINS","MT100",M->F2_VALINS)` ||||||||
82|F2_HORA|C|5|0|Hora|Hora|`99:99` |||||||||
83|F2_MOEDA|N|2|0|Moeda|Moeda da Fatura|`99` |`MaFisRef("NF_MOEDA","MT100",M->F2_MOEDA)` |1||N|||||
84|F2_REGIAO|C|3|0|Regiao|Regiao de Venda|||||N|||||
85|F2_VALCSLL|N|14|2|Valor CSLL|Valor CSLL|`@E 999,999,999.99` |`MaFisRef("NF_VALCSL","MT100",M->F2_VALCSLL)` |||N|||||
86|F2_VALCOFI|N|14|2|Valor COFINS|Valor COFINS|`@E 999,999,999.99` |`MaFisRef("NF_VALCOF","MT100",M->F2_VALCOFI)` |||N|||||
87|F2_VALPIS|N|14|2|Valor PIS|Valor PIS|`@E 999,999,999.99` |`MaFisRef("NF_VALPIS","MT100",M->F2_VALPIS)` |||N|||||
88|F2_LOTE|C|1|0|Doc. em Lote|Nota Fiscal em Lote|`@!` ||||N|||||
89|F2_TXMOEDA|N|11|4|Taxa Moeda|Taxa da Moeda|`@E 999999.9999` ||1||N|||||
90|F2_CLEOK|C|4|0|Flag CLe|Flag da capa de lote|||||N|A|R|||
91|F2_CHVCLE|C|14|0|Chave CLe|Chave da Capa de Lote|||||N|A|R|||
92|F2_IDCLE|C|12|0|ID_CLE|Identificacao da CLe|||||N|A|R|||
93|F2_VALIRRF|N|14|2|Valor IRRF|Valor do IRRF|`@e 999,999,999.99` |`MaFisRef("NF_VALIRR","MT100",M->F2_VALIRRF)` |||N|||||
94|F2_RECFAUT|C|1|0|Pag.Fret.Aut|Pagto do frete autonomo|`@!` |`MaFisRef("NF_RECFAUT","MT100",M->F2_RECFAUT)` |||||R|1=Emitente;2=Transportador||
95|F2_CARGA|C|6|0|Carga|Numero da Carga|`@!` ||||N|||||
96|F2_SEQCAR|C|2|0|Seq. Carga|Seq. Carga|`@!` ||||N|||||
97|F2_BASEINS|N|14|2|Base de INSS|Base de calculo do INSS|`@E 99,999,999.99` |`MaFisRef("NF_BASEINS","MT100",M->F2_BASEINS)` |||N|||||
98|F2_PEDPEND|C|6|0|Ped. Ent Fut|Pedido entrega futura|`@!` ||||N|||||
99|F2_DESCCAB|N|16|2|Indenizacao|Valor da Indenizacao|`@E 9,999,999,999,999.99` ||||N|||||
A0|F2_DTENTR|D|8|0|Data Entrega|Data de entrega||||||||||
A1|F2_FORMUL|C|1|0|Form. Prop.|Formulario Proprio|`!` |`Vazio().Or.Pertence("SN ")` |||N|||||
A2|F2_TIPODOC|C|2|0|Id. Doc.|Identificador de doc.||`MAFISREF("NF_TIPODOC","MT100",M->F2_TIPODOC)` |||N|||||
A3|F2_NFEACRS|C|9|0|NFE Acresc.|NFE de Acrescimo|`@!` ||||N|||||
A4|F2_TIPOREM|C|1|0|Tipo Remis.|Tipo da Remision|`@!` |`Pertence("0A") .AND.  Iif (FindFunction("A410LiqPro"),A410LiqPro(),.T.)` |"0"||N|||0=Venda;A=Consignacao||
A5|F2_SEQENT|C|6|0|Seq. Entrega|Sequencia de entrega||||||V||||
A6|F2_GRPDEP|C|5|0|Grupo Almox|Grupo de Almoxarifados|`@!` |`Vazio() .Or. ExistCpo("SX5","74"+M->F2_GRPDEP)` ||74|N|N|V|||
A7|F2_ICMSDIF|N|14|2|Icms. Dif.|Icms Diferido|`@E 99,999,999,999.99` |`Positivo().And.MafisRef("NF_ICMSDIF","MT460",M->F2_ICMSDIF)` |||N|||||
A8|F2_VALACRS|N|14|2|Vl.Acres.Fin|Valor do acrescimo financ|`@E 99,999,999,999.99` ||||N|||||
A9|F2_RECISS|C|1|0|Recolhe ISS|Indica se recolhe ISS||`MaFisRef("NF_RECISS","MT100",M->F2_RECISS)` ||||||||
B0|F2_CLIREM|C|6|0|Cli. Remessa|Cliente Remessa|`@!` |`Vazio() .Or. ExistCpo("SA1")` ||SA1|N|A|R|||
B1|F2_LOJAREM|C|2|0|Loja Remessa|Loja de Remessa|`@!` |`Vazio() .Or. ExistCpo("SA1",M->F2_CLIREM+M->F2_LOJAREM)` |||N|A|R|||
B2|F2_MUNPRES|C|7|0|Mun.Prest.|Municipio de Prestação|`@!` |||CC2SC5|S|A|R|||
B3|F2_ESTPRES|C|2|0|UF. Prest.|UF Prestação|`@!` |`Vazio() .or. ExistCpo("SX5","12"+M->F2_ESTPRES)` ||12|S|A|R|||
B4|F2_FILDEST|C|2|0|Filial Dest|Filial Destino|||||N|A|R|||
B5|F2_FLAGDEV|C|1|0|Flag. dev.|Flag devolucao total|`@!` ||||N|A|R|||
B6|F2_FORMDES|C|1|0|Form. Dest.|Formulario Destino|`@!` ||||N|||||
B7|F2_FRTCFOP|C|5|0|Frete CFOP|CFOP referente ao frete|`@!` ||||S|||||
B8|F2_HORNFE|C|8|0|Hora NF-e|Hora da emissão da NF-e|`@R 99:99:99` ||||S|A|R|||
B9|F2_HAWB|C|20|0|Processo|Processo do EEC|`@!` ||||||R|||
C0|F2_IDRECOP|C|6|0|Id Recopi|ID Solicitação RECOPI|`@!` ||||N|A|R|||
C1|F2_IDSA1|C|20|0|ID Hist. SA1|ID Hist. SA1|`@!` |`MaFisRef("NF_IDSA1","MT100",M->F2_IDSA1)` |||N||R|||
C2|F2_IDSA2|C|20|0|ID Hist. SA2|ID Hist. SA2|`@!` |`MaFisRef("NF_IDSA2","MT100",M->F2_IDSA2)` |||N||R|||
C3|F2_IDSED|C|20|0|ID Hist. SED|ID Hist. SED|`@!` |`MaFisRef("NF_IDSED","MT100",M->F2_IDSED)` |||N||R|||
C4|F2_DTESERV|D|8|0|Dt.Exec.Serv|Dt.Exec.Serviço|||||S|A|R|||
C5|F2_DIACTB|C|2|0|Cod.Diario|Cod.Diario Contabilidade|`@!` |`ExistCPO("CVL")` ||CVL|N|A|R|||
C6|F2_EMINFE|D|8|0|Emissão NF-e|Emissão da NF Eletrônica|`@D` ||||S|A|R|||
C7|F2_ESTCRED|N|16|2|Vlr Est Deb|Valor Estorno Débito|`@E 9,999,999,999,999.99` |`MaFisRef("NF_ESTCRED","MT100",M->F2_ESTCRED)` |||N|A|R|||
C8|F2_BSREIN|N|14|2|B.C.Reinteg|Base Calc.Reintegra|`@E 99,999,999,999.99` |`'MaFisRef("NF_BSREIN","MT100",M->F2_BSREIN)'` |||S|A|R|||
C9|F2_CREDNFE|N|16|2|Créd. Conced|Crédito concedido NF-e|`@E 9,999,999,999,999.99` ||||S|A|R|||
D0|F2_CODNFE|C|50|0|Cd.Ver. NF-e|Código verificação NF-e|`@!` ||||S|A|R|||
D1|F2_CHVNFE|C|44|0|Chave NFe|Chave da NFe SEFAZ|`@!` ||||N|A|R|||
D2|F2_CGCCLI|C|16|0|CPF/CNPJ|CPF/CNPJ do Cliente|`@R 99.999.999/9999-99` ||||N|A|R|||
D3|F2_BASPIS|N|14|2|Base PIS|Base PIS|`@E 999,999,999.99` |`MaFisRef("NF_BASEPIS","MT100",M->F2_BASPIS)` ||||||||
D4|F2_BASEIRR|N|16|2|Base IR|Valor da Base do IR|`@E 9,999,999,999,999.99` |`MaFisRef("NF_BASEIRR","MT100",M->F2_BASEIRR)` |||S|A|R|||
D5|F2_BASEPS3|N|14|2|Bs. Pis ST|Base Pis ST|`@E 999,999,999.99` |`Positivo().And.MaFisRef("NF_BASEPS3","MT100",M->F2_BASEPS3)` |||S|||||
D6|F2_BASEINA|N|14|2|Base INSS Ad|Base do INSS Cond. Espec.|`@E 99,999,999,999.99` |`MaFisRef("NF_BASEINA","MT100",M->F2_BASEINA)` |||N|A|R|||
D7|F2_BASECF3|N|14|2|Bs. Cof ST|Base Cofins ST|`@E 999,999,999.99` |`Positivo().And.MaFisRef("NF_BASECF3","MT100",M->F2_BASECF3)` |||S|||||
D8|F2_BASECPM|N|14|2|Bs.ISS CPM|Base ISS CPM|`@E 99,999,999,999.99` |`MaFisRef("NF_BASECPM","MT100",M->F2_BASECPM)` ||||||||
D9|F2_BASEFMP|N|14|2|Base FUMIPEQ|Base de Cálculo FUMIPEQ|`@E 99,999,999,999.99` |`MaFisRef("NF_BASEFMP","MT100",M->F2_BASEFMP)` ||||||||
E0|F2_MENNOTA|C|60|0|Mens.p/Nota|Mensagem para Nota||`Vazio() .OR. Texto()` |||N|A|R|||
E1|F2_NFELETR|C|20|0|NF Eletr.|Nota Fiscal Eletrônica|`@!` ||||S|A|R|||
E2|F2_LTRAN|C|41|0|Fonte Lei Tr|Fonte Lei Transparência|`@!` ||||N|V|R|||
E3|F2_RECOPI|C|1|0|Flag RECOPI|Flag NF RECOPI|`@!` |||||A||||
E4|F2_NUMORC|C|6|0|No Orcamento|Numero do Orcamento|`@!` ||||N|V|R|||
E5|F2_ORDSEP|C|6|0|Ordem Sep.|Ordem de Separação|||||N|V|R|||
E6|F2_NODIA|C|10|0|Seq.Diario|Seq.Diario Contabilidade|`@!` ||||N|V|R|||
E7|F2_TIPORET|C|1|0|Retorno|Tipo de Retorno|`@!` |`Pertence("1|2| ")` ||||||1=Automatico;2=Manual||
E8|F2_TOTEST|N|14|2|Crg.Trb.Est|Carga Tributária Estadual|`@E 99,999,999,999.99` ||||N|A|R|||
E9|F2_TOTFED|N|14|2|Crg.Trb.Fed|Carga Tributária Federal|`@E 99,999,999,999.99` ||||N|A|R|||
F0|F2_SERSAT|C|9|0|Série SAT|Número de Série do SAT|`@!` |||||||||
F1|F2_STATUS|C|3|0|Status NFE|Status Canc. NFE||||||A|R|||
F2|F2_TIPIMP|C|1|0|Cons.Cg.Trb|Consulta Carga Tributaria|`@!` ||||N|A|R|||
F3|F2_TOTMUN|N|14|2|Crg.Trb.Mun|Carga Tributária Municipa|`@E 99,999,999,999.99` ||||N|A|R|||
F4|F2_TPCOMPL|C|1|0|Tipo Compl.|Tipo de Complemento|`@!` ||||N|V|R|1=Preço; 2=Quantidade||
F5|F2_TPFRETE|C|1|0|Tipo de fret|Indica tipo de frete|`@!` ||||S|V|R|||
F6|F2_VALCF3|N|14|2|Vl. COF ST|Valor Cofins ST|`@E 999,999,999.99` |`Positivo().And.MaFisRef("NF_VALCF3","MT100",M->F2_VALCF3)` |||S|||||
F7|F2_VALFAC|N|14|2|Vl.Facs|Valor do Facs|`@E 99,999,999,999.99` |`MaFisRef("NF_VALFAC","MT100",M->F2_VALFAC)` |||N|A|R|||
F8|F2_VALFET|N|14|2|Vl.Fethab|Valor do Fethab|`@E 99,999,999,999.99` |`MaFisRef("NF_VALFET","MT100",M->F2_VALFET)` |||N|A|R|||
F9|F2_VALFMD|N|14|2|Vl.Famad|Valor do Famad|`@E 99,999,999,999.99` |`MaFisRef("NF_VALFMD","MT100",M->F2_VALFMD)` ||||||||
G0|F2_VALFMP|N|14|2|Vl.FUMIPEQ|Valor do Fumipeq|`@E 99,999,999,999.99` |`MaFisRef("NF_VALFMP","MT100",M-> F2_VALFMP)` ||||||||
G1|F2_VALPS3|N|14|2|Vl. Pis ST|Valor Pis ST|`@E 999,999,999.99` |`Positivo().And.MaFisRef("NF_VALPS3","MT100",M->F2_VALPS3)` |||S|||||
G2|F2_VALTST|N|14|2|Val. ST tran|Valor ICMS ST transporte|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("NF_VALTST","MT100",M->F2_VALTST)` |||N|A|R|||
G3|F2_VEICUL1|C|8|0|Veiculo 1|Codigo do Veiculo 1|`@!` |||DA3|N|||||
G4|F2_VEICUL2|C|8|0|Veiculo 2|Codigo do Veiculo 2|`@!` |||DA3|N|||||
G5|F2_VALINA|N|14|2|Vlr INSS Ad|Vlr.INSS.Cond.Espec.|`@E 99,999,999,999.99` |`MaFisRef("NF_VALINA","MT100",M->F2_VALINA)` |||N|A|R|||
G6|F2_VLCPM|N|14|2|Vl.ISS CPM|Valor ISS CPM|`@E 99,999,999,999.99` |`MaFisRef("NF_VALCPM","MT100",M->F2_VLCPM)` ||||||||
G7|F2_VLR_FRT|N|12|2|Frete Pauta|Valor do Frete de Pauta|`@E 999,999,999.99` |`MaFisRef("NF_VLR_FRT","MT100",M->F2_VLR_FRT)` |||N|A|R|||
G8|F2_VLSENAR|N|14|2|Valor Senar|Valor do Senar|`@E 99,999,999,999.99` |`MaFisRef("NF_VLSENAR","MT100",M->F2_VLSENAR)` |||N|A||||
G9|F2_VREINT|N|14|2|V.Reintegra|Valor Reintegra|`@E 99,999,999,999.99` |`'MaFisRef("NF_VREINT","MT100",M->F2_VREINT)'` |||S|A|R|||
H0|F2_VALIMA|N|14|2|Vlr. IMA-MT|Valor do IMA-MT|`@E 99,999,999,999.99` |`MaFisRef("NF_VALIMA","MT100",M->F2_VALIMA)` |||S|A|R|||
H1|F2_VEICUL3|C|8|0|Veiculo 3|Codigo do Veiculo 3|`@!` |||DA3|N|||||
H2|F2_VALFUND|N|14|2|Vlr.FUNDESA|Valor do FUNDESA|`@E 99,999,999,999.99` |`MaFisRef("NF_VALFUND","MT100",M->F2_VALFUND)` |||S|A|R|||
H3|F2_VALFASE|N|14|2|Vlr.FASE-MT|Valor do FASE-MT|`@E 99,999,999,999.99` |`MaFisRef("NF_VALFASE","MT100",M->F2_VALFASE)` |||S|A|R|||
H4|F2_VALFDS|N|14|2|Vl.Fundersul|Valor do Fundersul|`@E 99,999,999,999.99` |`MaFisRef("NF_VALFDS","MT100",M->F2_VALFDS)` |||N|A|R|||
H5|F2_VALFAB|N|14|2|Vl.Fabov|Valor do Fabov|`@E 99,999,999,999.99` |`MaFisRef("NF_VALFAB","MT100",M->F2_VALFAB)` |||N|A|R|||
H6|F2_TXREF|N|11|4|Taxa Cambial|taxa Cambial|`@E 999,999.9999` |||||||||
H7|F2_UFDEST|C|2|0|UF Destino|UF Destino|`@!` |`MaFisRef("NF_UFDEST","MT100",M->F2_UFDEST)` |||N|A|R|||
H8|F2_UFORIG|C|2|0|UF Origem|UF Origem|`@!` |`MaFisRef("NF_UFORIGEM","MT100",M->F2_UFORIG)` |||N|A|R|||
H9|F2_SERSUBS|C|3|0|Serie Subst.|Serie da NF Substituida|`!!!` ||||N|A|R|||
I0|F2_TOTIMP|N|14|2|Tot.Cg.Trb.|Total Carga Tributaria.|`@E 99,999,999,999.99` ||||N|A|R|||
I1|F2_SERMDF|C|3|0|Serie MDFe|Serie do MDFe|`!!!` ||||S|A|R|||
I2|F2_PREFORI|C|3|0|Pref Origem|Prefixo Origem|`@!` ||||N|A|R|||
I3|F2_REFMOED|N|2|0|Ref.Moeda|Moeda Referência|`99` ||||N|A|R|||
I4|F2_REFTAXA|N|11|4|Ref.Taxa|Taxa Referência|`@E 999999.9999` |`Positivo()` |||N|A|R|||
I5|F2_SDOC|C|3|0|Série Doc.|Série do Documento Fiscal|`!!!` ||||N|V|R|||
I6|F2_SDOCMAN|C|3|0|Série Manual|Série Doc. Manual|`!!!` ||||N|V|R|||
I7|F2_SDOCMDF|C|3|0|Série MDFe|Série do MDFe|`!!!` ||||N|V|R|||
I8|F2_SDOCNXT|C|3|0|Prox. Série|Proxima Série|`!!!` ||||N|V|R|||
I9|F2_SDOCORI|C|3|0|Sér.Original|Série Orig. Qdo Devolucao|`!!!` ||||N|V|R|||
J0|F2_SDOCSUB|C|3|0|Série Subst.|Série da NF Substituida|`!!!` ||||N|V|R|||
J1|F2_NTFECP|C|12|0|Cod.NT Fecp|Cod.NumTit Fecp|`@!` ||||S|||||
J2|F2_NUMMDF|C|9|0|Número MDFe|Número do MDFe vinculado|`@!` ||||S|A|R|||
J3|F2_NFSUBST|C|9|0|Nf Subst.|NF Substituida|`@!` ||||N|A|R|||
J4|F2_PAFMD5|C|32|0|MD5|Chave MD5 do Registro||||||A|R|||
J5|F2_LOJARET|C|2|0|Lj. Retirada|Loja de Retirada|`@!` |||||||||
J6|F2_LOJENT|C|2|0|Loja Entrega|Loja Entrega|`@!` ||||N|A|R|||
J7|F2_LOJADES|C|2|0|Loja Dest.|Loja Destino|`@!` ||||N|||||
J8|F2_NFICMST|C|12|0|Cod.NF IcmSt|Codigo ICMS ST pela NFS|`@!` ||||S|A|R|||
J9|F2_BASEFUN|N|14|2|Bas.FUNRURAL|Base do FUNRURAL|`@E 99,999,999,999.99` |`MaFisRef("NF_BASEFUN","MT100",M->F2_BASEFUN)` |||N|V|R|||
K0|F2_BASETST|N|14|2|Base ST tran|Base ICMS ST transporte|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("NF_BASETST","MT100",M->F2_BASETST)` |||N|A|R|||
K1|F2_BASFECP|N|14|2|Base FCP Pr.|Base FCP Próprio|`@E 99,999,999,999.99` |`MaFisRef("NF_BASFECP","MT100",M->F2_BASFECP)` |||S|A|R|||
K2|F2_BSFCCMP|N|14|2|Base FCP Cmp|Base FCP Complementar|`@E 99,999,999,999.99` |`MaFisRef("NF_BSFCCMP","MT100",M->F2_BSFCCMP)` |||S|A|R|||
K3|F2_BSFCPST|N|14|2|Base FCP ST|Base FCP ST|`@E 99,999,999,999.99` |`MaFisRef("NF_BSFCPST","MT100",M->F2_BSFCPST)` |||S|A|R|||
K4|F2_CLIENT|C|6|0|Cliente Entr|Cliente Entrega|`@!` ||||N|A|R|||
K5|F2_CLIRET|C|6|0|Cli.Retirada|Cliente de Retirada|`@!` |||||||||
K6|F2_CMUNDE|C|5|0|Mun. Dest.|Mun. Dest.|`@99999` ||||N|A|R|||
K7|F2_CMUNOR|C|5|0|Mun.Origem|Mun.Origem|`@99999` ||||N|A|R|||
K8|F2_CNO|C|6|0|Cod CNO|Codigo CNO||`Vazio() .Or. ExistCpo('SON',M->F2_CNO )` ||SON|N|A|R|||
K9|F2_BASCOFI|N|14|2|Base COFINS|Base COFINS|`@E 999,999,999.99` |`MaFisRef("NF_BASECOF","MT100",M->F2_BASCOFI)` ||||||||
L0|F2_BASCSLL|N|14|2|Base CSLL|Base CSLL|`@E 999,999,999.99` |`MaFisRef("NF_BASECSL","MT100",M->F2_BASCSLL)` ||||||||
L1|F2_CODRGS|C|1|0|Status RGS|Status registro saida|||||N|A|R|||
L2|F2_DAUTNFE|D|8|0|Data de Auto|Data de Autorizacao da NF|||||N|A|R|||
L3|F2_DESCZFR|N|14|2|Desc.ZFM|Desc. Zona Franca Manaus|`@E 99,999,999,999.99` |`MaFisRef("NF_DESCZF","MT100",M->F2_DESCZFR)` |||N|A|R|||
L4|F2_DTDIGIT|D|8|0|Data digit.|Data de digitacao|||||S|V|R|||
L5|F2_DTTXREF|D|8|0|Dt.R.Cambial|Data Referencia Cambial|||||S|V|R|||
L6|F2_IDRGS|C|54|0|Id RGS|Id do Registro de saída|||||N|A|R|||
L7|F2_IDNF|C|36|0|ID da NF|ID da Nota Fiscal|`@!` ||||N|V|R|||
L8|F2_IDCCE|C|54|0|Id CC-e|Id da CC-e|||||N|A|R|||
L9|F2_HAUTNFE|C|5|0|Hora de Auto|Hora de Autorizacao da NF|||||N|A|R|||
M0|F2_GNRDIF|C|12|0|GNRE DIFAL|DIFAL da UF de destino|`@!` ||||S|A|R|||
M1|F2_GNRFECP|C|12|0|GNRE FECP|FECP da UF de destino|`	 @!` ||||S|A|R|||
M2|F2_FLAGRGS|C|4|0|Flag RGS|Flag do Registro de saída|||||N|A|R|||
M3|F2_FORDES|C|6|0|Forn. Dest.|Fornecedor Destino|`@!` ||||N|||||
M4|F2_EVENFLG|C|1|0|Flag CCe|Flag da carta de correcao|||||N|A|R|||


## SIX - Índices da tabela

ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|F2_FILIAL+F2_DOC+F2_SERIE+F2_CLIENTE+F2_LOJA+F2_FORMUL+F2_TIPO|Numero + Serie Docto. + Cliente + Loja + Form. Prop. + Tipo da nota|XXX+XXX+SA1||S|
2|F2_FILIAL+F2_CLIENTE+F2_LOJA+F2_DOC+F2_SERIE+F2_TIPO+F2_ESPECIE|Cliente + Loja + Numero + Serie Docto. + Tipo da nota + Espec.Docum.|SA1||S|
3|F2_FILIAL+F2_ECF+DTOS(F2_EMISSAO)+F2_PDV+F2_SERIE+F2_MAPA+F2_DOC|Serie ECF + DT Emissao + Numero PDV + Serie Docto. + Numero MAPA + Num|||S|
4|F2_FILIAL+F2_SERIE+DTOS(F2_EMISSAO)+F2_DOC+F2_CLIENTE+F2_LOJA|Serie Docto. + DT Emissao + Numero + Cliente + Loja|XXX+XXX+XXX+SA1||S|
5|F2_FILIAL+F2_CARGA+F2_SEQCAR+F2_SERIE+F2_DOC+F2_CLIENTE+F2_LOJA|Carga + Seq. Carga + Serie Docto. + Numero + Cliente + Loja|||S|
6|F2_FILIAL+F2_SERIORI+F2_NFORI|Sér.Original + Docto. Orig.|XXX+XXX||S|
7|F2_FILIAL+F2_HAWB|Processo|XXX+XXX||S|
8|F2_FILIAL+F2_NFELETR+DTOS(F2_EMINFE)+F2_CLIENTE+F2_LOJA|NF Eletr. + Emissão NF-e + Cliente + Loja|XXX+XXX+SA1||S|
9|F2_FILIAL+F2_NODIA|Seq.Diario|||S|
B|F2_FILIAL+F2_DOC+F2_SDOC+F2_CLIENTE+F2_LOJA+F2_FORMUL+F2_TIPO|Numero + Série Doc. + Cliente + Loja + Form. Prop. + Tipo da nota|XXX+XXX+SA1||N|
C|F2_FILIAL+F2_CLIENTE+F2_LOJA+F2_DOC+F2_SDOC|Cliente + Loja + Numero + Série Doc.|SA1||N|
D|F2_FILIAL+F2_ECF+DTOS(F2_EMISSAO)+F2_PDV+F2_SDOC+F2_MAPA+F2_DOC|Serie ECF + DT Emissao + Numero PDV + Série Doc. + Numero MAPA + Numer|||N|
E|F2_FILIAL+F2_SDOC+DTOS(F2_EMISSAO)+F2_DOC+F2_CLIENTE+F2_LOJA|Série Doc. + DT Emissao + Numero + Cliente + Loja|XXX+XXX+XXX+SA1||N|
F|F2_FILIAL+F2_CARGA+F2_SEQCAR+F2_SDOC+F2_DOC+F2_CLIENTE+F2_LOJA|Carga + Seq. Carga + Série Doc. + Numero + Cliente + Loja|||N|
G|F2_FILIAL+F2_SDOCORI+F2_NFORI|Sér.Original + Docto. Orig.|XXX+XXX||N|
H|F2_FILIAL+DTOS(F2_EMISSAO)+F2_HORA|DT Emissao + Hora|||S|
J|F2_FILIAL+F2_IDNF|ID da NF|||S|


