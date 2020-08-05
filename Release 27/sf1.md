# SF1 - Cabeçalho das NF de Entrada
## SX3 - Campos da tabela

X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|F1_FILIAL|C|2|0|Filial|Filial do Sistema|||||S|A|R|||
02|F1_DOC|C|9|0|Numero|Numero do documento|`@!` ||||S|||||
03|F1_SERIE|C|3|0|Serie|Serie do Documento|`!!!` ||||S|||||
04|F1_FORNECE|C|6|0|Fornecedor|Codigo do fornecedor|`@!` |||FOR|S|||||
05|F1_LOJA|C|2|0|Loja|Loja do fornecedor|`@!` ||||S|||||
06|F1_COND|C|3|0|Cond. Pagto|Codigo da condic. de pgto||||SE4|S|||||
07|F1_DUPL|C|9|0|Num. Titulo|Numero do titulo|`@!` ||||N|||||
08|F1_EMISSAO|D|8|0|DT Emissao|Data de Emissao da NF|||ddatabase||N|||||
09|F1_EST|C|2|0|Estado|Estado de emissao da NF|`@!` |`ExistCpo("SX5","12"+M->F1_EST).And.MaFisRef("NF_UFORIGEM","MT100",M->F1_EST)` |||N|||||
10|F1_FRETE|N|15|2|Vlr.Frete|Valor do frete|`@E 999,999,999.99` |`MaFisRef("NF_FRETE","MT100",M->F1_FRETE)` |||N|||||
11|F1_DESPESA|N|15|2|Vlr.Despesas|Valor das despesas|`@E 999,999,999.99` |`MaFisRef("NF_DESPESA","MT100",M->F1_DESPESA)` |||N|||||
12|F1_BASEICM|N|14|2|Base p/ICMS|Base de calculo para ICM|`@E 999,999,999.99` |`MaFisRef("NF_BASEICM","MT100",M->F1_BASEICM)` |||N|||||
13|F1_VALICM|N|14|2|Vlr.ICMS|Valor do ICMS|`@E 999,999,999.99` |`MaFisRef("NF_VALICM","MT100",M->F1_VALICM)` |||N|||||
14|F1_BASEIPI|N|14|2|Base p/IPI|Base de calculo para IPI|`@E 999,999,999.99` |`MaFisRef("NF_BASEIPI","MT100",M->F1_BASEIPI)` |||N|||||
15|F1_VALIPI|N|14|2|Vlr.IPI|Valor do IPI|`@E 999,999,999.99` |`MaFisRef("NF_VALIPI","MT100",M->F1_VALIPI)` |||N|||||
16|F1_VALMERC|N|14|2|Vlr.Mercad|Valor da nercadoria|`@E 99,999,999,999.99` |`MaFisRef("NF_VALMERC","MT100",M->F1_VALMERC)` |||N|||||
17|F1_VALBRUT|N|14|2|Vlr.Bruto|Valor bruto da NF|`@E 99,999,999,999.99` |`MaFisRef("NF_TOTAL","MT100",M->F1_VALBRUT)` |||N|||||
18|F1_TIPO|C|1|0|Tipo da Nota|Nota/Consumidor/Ticket...|`@!` |`pertence("NDIPBC")` |||N|||||
19|F1_DESCONT|N|14|2|Descontos|Descontos da nota fiscal|`@E 999,999,999.99` |`MaFisRef("NF_DESCONTO","MT100",M->F1_DESCONT)` |||N|||||
20|F1_DTDIGIT|D|8|0|Dt.Digitacao|Data de Digitacao|||ddatabase||N|||||
21|F1_CPROVA|C|14|0|Arq.C.Prova|Nome Arq. de Contra Prova|||ddatabase||N|||||
22|F1_NUMTRIB|C|9|0|Rl. SF1xSE2|Relac. SF1 x SE2|`@!` ||||N|V||||
23|F1_BRICMS|N|14|2|Base ICM Sol|Base ICMS Solidario|`@E 999,999,999.99` |`MaFisRef("NF_BASESOL","MT100",M->F1_BRICMS)` |||N|||||
24|F1_ICMSRET|N|14|2|ICMS Solid.|Valor ICMS Solidario|`@E 999,999,999.99` |`MaFisRef("NF_VALSOL","MT100",M->F1_ICMSRET)` |||N|||||
25|F1_BASEFD|N|14|2|Base Fr. Des|Base do Frete e Despesas|`@E 999,999,999.99` ||||N|||||
26|F1_DTLANC|D|8|0|Dt.Lancto|Data de Lancamento|||||N|||||
27|F1_OK|C|2|0|Ok|Ok Lancto. Conhec. Frete|||||N|||||
28|F1_ORIGLAN|C|2|0|Orig.Lancto.|Origem do Lancamento|||||N|||||
29|F1_TX|C|1|0|Transmissao|Flag para Transmissao|`!` ||||N|||||
30|F1_CONTSOC|N|14|2|Vl.Cont.Soc.|Valor Contr.Segur.Social|`@E 999,999,999.99` |`MaFisRef("NF_FUNRURAL","MT100",M->F1_CONTSOC)` |||N|||||
31|F1_IRRF|N|14|2|Imp. Renda|Imposto de Renda|`@E 999,999,999.99` |`MaFisRef("NF_VALIRR","MT100",M->F1_IRRF)` |||N|||||
32|F1_FORMUL|C|1|0|Form. Prop.|Formulario Proprio|`!` |`Vazio().Or.Pertence("SN ")` |||N|||||
33|F1_NFORIG|C|9|0|Doc.Despesa|Documento de Despesa|`@!` |||||V||||
34|F1_SERORIG|C|3|0|Ser.despesa|Serie do Docto.de Despesa|`!!!` |||||V||||
35|F1_ESPECIE|C|5|0|Espec.Docum.|Espécie do Documento|`@!` |`Vazio() .or. ExistCpo("SX5","42"+M->F1_ESPECIE)` ||42||||||
36|F1_IMPORT|C|1|0|Flag Import|Flag de Importacao|||||N|||||
37|F1_II|N|14|2|Vlr.Imp.Impo|Vlr.Imposto de Importacao|`@E 99,999,999,999.99` |`MaFisRef("NF_VALII","MT100",M->F1_II)` |||N|||||
38|F1_REMITO|C|9|0|N§ Remito|Campo para Localizaçöes|`@!` ||||N|A||||
39|F1_BASIMP2|N|14|2|Base Imp. 2|Base de Calculo Imposto 2|`@E  99,999,999,999.99` |`MaFisRef("NF_BASEIV2","MT100",M->F1_BASIMP2)` |||N|||||
40|F1_BASIMP3|N|14|2|Base Imp. 3|Base de Calculo Imposto 3|`@E  99,999,999,999.99` |`MaFisRef("NF_BASEIV3","MT100",M->F1_BASIMP3)` |||N|||||
41|F1_BASIMP4|N|14|2|Base Imp. 4|Base de Calculo Imposto 4|`@E  99,999,999,999.99` |`MaFisRef("NF_BASEIV4","MT100",M->F1_BASIMP4)` |||N|||||
42|F1_BASIMP5|N|14|2|Base Imp. 5|Base de Calculo Imposto 5|`@E  99,999,999,999.99` |`MaFisRef("NF_BASECF2","MT100",M->F1_BASIMP5)` |||N|||||
43|F1_BASIMP6|N|14|2|Base Imp. 6|Base de Calculo Imposto 6|`@E  99,999,999,999.99` |`MaFisRef("NF_BASEPS2","MT100",M->F1_BASIMP6)` |||N|||||
44|F1_VALIMP1|N|14|2|Valor Imp. 1|Valor do Imposto 1|`@E  99,999,999,999.99` |`MaFisRef("NF_VALIV1","MT100",M->F1_VALIMP1)` |||N|||||
45|F1_VALIMP2|N|14|2|Valor Imp. 2|Valor do Imposto 2|`@E  99,999,999,999.99` |`MaFisRef("NF_VALIV2","MT100",M->F1_VALIMP2)` |||N|||||
46|F1_VALIMP3|N|14|2|Valor Imp. 3|Valor do Imposto 3|`@E  99,999,999,999.99` |`MaFisRef("NF_VALIV3","MT100",M->F1_VALIMP3)` |||N|||||
47|F1_VALIMP4|N|14|2|Valor Imp. 4|Valor do Imposto 4|`@E  99,999,999,999.99` |`MaFisRef("NF_VALIV4","MT100",M->F1_VALIMP4)` |||N|||||
48|F1_VALIMP5|N|14|2|Valor Imp. 5|Valor do Imposto 5|`@E  99,999,999,999.99` |`MaFisRef("NF_VALCF2","MT100",M->F1_VALIMP5)` |||N|||||
49|F1_VALIMP6|N|14|2|Valor Imp. 6|Valor do Imposto 6|`@E  99,999,999,999.99` |`MaFisRef("NF_VALPS2","MT100",M->F1_VALIMP6)` |||N|||||
50|F1_ORDPAGO|C|6|0|Ordem Pagto|Ordem de Pagamento|`@!` ||||N|||||
51|F1_HORA|C|8|0|Hora|Hora|`99:99:99` ||||N|||||
52|F1_INSS|N|14|2|Valor INSS|Valor do INSS|`@E 999,999,999.99` |`MaFisRef("NF_VALINS","MT100",M->F1_INSS)` |||N|||||
53|F1_ISS|N|14|2|Valor ISS|Valor do ISS|`@E 999,999,999.99` |`MaFisRef("NF_VALISS","MT100",M->F1_ISS)` |||N|||||
54|F1_BASIMP1|N|14|2|Base Imp. 1|Base de Calculo Imposto 1|`@E  99,999,999,999.99` |`MaFisRef("NF_BASEIV1","MT100",M->F1_BASIMP1)` |||N|||||
55|F1_HAWB|C|20|0|No. Conhec.|No. Conhec.|`@!` ||||S|||||
56|F1_TIPO_NF|C|1|0|Tipo Docto.|Tipo Docto. - Importacao|`@!` ||||N|||||
57|F1_IPI|N|15|2|Aliq. IPI|Alíquota de IPI|`@E 99.99` ||||N|||||
58|F1_ICMS|N|15|2|ICMS|ICMS|`@E 999,999,999,999.99` ||||N|||||
59|F1_PESOL|N|11|4|Peso Liquido|Peso Liquido|`@E 999,999.9999` ||||N|||||
60|F1_FOB_R|N|15|2|FOB|FOB|`@E 999,999,999,999.99` ||||N|||||
61|F1_SEGURO|N|15|2|Vlr.Seguro|Vlr.Seguro|`@E 999,999,999,999.99` |`MaFisRef("NF_SEGURO","MT100",M->F1_SEGURO)` |||N|||||
62|F1_CIF|N|15|2|C.I.F.|C.I.F.|`@E 999,999,999,999.99` ||||N|||||
63|F1_MOEDA|N|2|0|Moeda|Moeda da Fatura|`@E 99` |`MaFisRef("NF_MOEDA","MT100",M->F1_MOEDA)` |1||N|||||
64|F1_PREFIXO|C|3|0|Prefixo|Prefixo da Duplicata|`@!` ||||N|||||
65|F1_STATUS|C|1|0|Status|Status da NF|`@!` ||||N|V||||
66|F1_VALEMB|N|14|2|Vl.Embalagem|Valor da Embalagem|`@E 99,999,999.99` |`MaFisRef("NF_VALEMB","MT100",M->F1_VALEMB)` |||N|||||
67|F1_RECBMTO|D|8|0|Dt. Receb.|Data de Recebimento|||||N|||||
68|F1_CTR_NFC|C|12|0|Contr. N.F.C|Controle de N.F.C|`@!` ||||N|||||
69|F1_APROV|C|6|0|Gr Aprovacäo|Grupo de Aprovador|||||N|V|R||`.F.` |
70|F1_TXMOEDA|N|11|4|Taxa Moeda|Taxa da Moeda|`@E 999999.9999` ||1||N|||||
71|F1_PEDVEND|C|6|0|Ped. vendas|Pedido de vendas gerado|||||N|||||
72|F1_SUBSERI|C|3|0|Subserie|Subserie do documento|`!!!` ||||N|A|R|||
73|F1_TIPODOC|C|2|0|Id. Doc.|Identificador de doc.||`MAFISREF("NF_TIPODOC","MT100",M->F1_TIPODOC)` |||N|||||
74|F1_DOCISEN|C|9|0|Doc.Fol.Isen|Documento Folha Isento|`@!` ||||S|V|R|||
75|F1_VERBAIS|C|9|0|Verba Isen.|Verba Folha Isento|`@!` ||||S|V|R|||
76|F1_TIPOREM|C|1|0|Tipo Remito|Tipo do Remito|`@!` |`Pertence("0A")` |||N|||0=Compra;A=Consignacao||
77|F1_GNR|C|6|0|GNRE|Guia Nac. Recolhimento||||||||||
78|F1_ORIGEM|C|8|0|Origem|Origem|`@!` ||||N|V|R|||
79|F1_PLACA|C|8|0|Placa|Placa Veiculo|`@!` ||||N|A|R|||
80|F1_VALPIS|N|12|2|Valor do PIS|PIS Retenção|`@e 999,999,999.99` |`MaFisRef("NF_VALPIS","MT100",M->F1_VALPIS)` ||||V|R|||
81|F1_VALCOFI|N|12|2|Vlr.COFINS|Vlr.Retenção do COFINS|`@e 999,999,999.99` |`MaFisRef("NF_VALCOF","MT100",M->F1_VALCOF)` ||||V|R|||
82|F1_VALCSLL|N|12|2|Vlr.CSLL|Vlr.Retenção CSLL|`@e 999,999,999.99` |`MaFisRef("NF_VALCSL","MT100",M->F1_VALCSLL)` ||||V|R|||
83|F1_BASEPS3|N|14|2|Bs. Pis ST|Base Pis ST|`@E 999,999,999.99` |`Positivo().And.MaFisRef("NF_BASEPS3","MT100",M->F1_BASEPS3)` |||N|||||
84|F1_VALPS3|N|14|2|Vl. Pis ST|Valor Pis ST|`@E 999.999.999,99` |`Positivo().And.MaFisRef("NF_VALPS3","MT100",M->F1_VALPS3)` |||N|||||
85|F1_BASECF3|N|14|2|Bs. Cof ST|Base Cofins ST|`@E 999,999,999.99` |`Positivo().And.MaFisRef("NF_BASECF3","MT100",M->F1_BASECF3)` |||N|||||
86|F1_VALCF3|N|14|2|Vl. Cof ST|Valor Cofins ST|`@E 999,999,999.99` |`Positivo().And.MaFisRef("NF_VALCF3","MT100",M->F1_VALCF3)` |||N|||||
87|F1_NFELETR|C|20|0|NF Eletr.|Nota Fiscal Eletrônica|`@!` ||||S|A|R|||
88|F1_EMINFE|D|8|0|Emissão NF-e|Emissão da NF Eletrônica|`@d` ||||S|A|R|||
89|F1_HORNFE|C|8|0|Hora NF-e|Hora da emissão da NF-e|`@R 99:99:99` ||||S|A|R|||
90|F1_CODNFE|C|50|0|Cd.Ver. NF-e|Código verificação NF-e|`@!` ||||S|A|R|||
91|F1_CREDNFE|N|16|2|Créd. Conced|Crédito concedido NF-e|`@E 9,999,999,999,999.99` ||||S|A|R|||
92|F1_VNAGREG|N|16|2|Val.N.Agreg.|Valor não agregado total|`@E 9,999,999,999,999.99` |`MaFisRef("NF_VNAGREG","MT100",M->F1_VNAGREG)` |||N|A|R|||
93|F1_NUMRPS|C|12|0|Num. RPS|Número do RPS|`@!` ||||S|A|R|||
94|F1_VALIRF|N|14|2|IRRF Ret|Valor do IRRF Retido|`@E 999,999,999.99` ||||N|A|R|||
95|F1_NUMMOV|C|2|0|Movimento|Movimento do Dia|||||N|A|R|||
96|F1_CHVNFE|C|44|0|Chave NFe|Chave da NFe SEFAZ|`@!` ||||N|A|R|||
97|F1_RECISS|C|1|0|Rec Iss|Recolhe ISS ?|`@!` |`MAFISREF("NF_RECISS","MT100",M->F1_RECISS)` |||N|A|R|1=Sim;2=Nao||
98|F1_FILORIG|C|2|0|Filial Orig|Filial de Origem|||||N|A|R|||
99|F1_ESTCRED|N|16|2|Vlr Est Cred|Valor Estorno Credito|`@E 9,999,999,999,999.99` |`MaFisRef("NF_ESTCRED","MT100",M->F1_ESTCRED)` |||N|A|R|||
A0|F1_NODIA|C|10|0|Seq. Diário|Seq. Diário Contabilidade|`@!` |||||||||
A1|F1_DIACTB|C|2|0|Cód Diário|Cód Diário Contabilidaded|`@!` |`ExistCPO("CVL")` ||CVL||||||
A2|F1_NUMRA|C|6|0|Cód Func|Código do funcionário|`@!` |||||||||
A3|F1_BASEINS|N|14|2|Base de INSS|Base de cálculo do INSS|`@E 99,999,999,999.99` |`MaFisRef("NF_BASEINS","MT100",M->F1_BASEINS)` |||N|A|R|||
A4|F1_VALFDS|N|14|2|Vl.Fundersul|Valor do Fundersul|`@E 999,999,999.99` |`MaFisRef("NF_VALFDS","MT100",M->F1_VALFDS)` |||N|A|R|||
A5|F1_TRANSP|C|6|0|Transp.|Codigo da Transportadora|`@!` |`Vazio() .Or. ExistCPO('SA4',M->F1_TRANSP,1)` ||SA4|N|A|R|||
A6|F1_PLIQUI|N|14|5|Peso Liquido|Peso Liquido da N.F.|`@E 99,999,999.99999` ||||N|A|R|||
A7|F1_PBRUTO|N|11|4|Peso Bruto|Peso Bruto da N.F.|`@E 999999.9999` ||||N|A|R|||
A8|F1_ESPECI1|C|10|0|Especie 1|Especie 1|`@!` ||||N|A|R|||
A9|F1_VOLUME1|N|6|0|Volume 1|Volume 1|`@E 999999` ||||N|A|R|||
B0|F1_ESPECI2|C|10|0|Especie 2|Especie 2|`@!` ||||N|A|R|||
B1|F1_VOLUME2|N|6|0|Volume 2|Volume 2|`@E 999999` ||||N|A|R|||
B2|F1_ESPECI3|C|10|0|Especie 3|Especie 3|`@!` ||||N|A|R|||
B3|F1_VOLUME3|N|6|0|Volume 3|Volume 3|`@E 999999` ||||N|A|R|||
B4|F1_ESPECI4|C|10|0|Especie 4|Especie 4|`@!` ||||N|A|R|||
B5|F1_VOLUME4|N|6|0|Volume 4|Volume 4|`@ 999999` ||||N|A|R|||
B6|F1_MOTIVO|C|14|0|Motivo Devol|Motivo Aprov/Rej AFIP|`@!` ||||N|||||
B7|F1_VALIMA|N|14|2|Vlr. IMA-MT|Valor do IMA-MT|`@E 99,999,999,999.99` |`MaFisRef("NF_VALIMA","MT100",M->F1_VALIMA)` ||||A|R|||
B8|F1_VALFUND|N|14|2|Vlr.FUNDESA|Valor do FUNDESA|`@E 99,999,999,999.99` |`MaFisRef("NF_VALFUND","MT100",M->F1_VALFUND)` ||||A|R|||
B9|F1_CLIDEST|C|6|0|Cliente Dest|Cliente de Destino|`@!` |`MaFisRef("NF_CLIDEST","MT100",M->F1_CLIDEST)` ||SA1|N|A|R|||
C0|F1_VALFASE|N|14|2|Vlr.FASE-MT|Valor do FASE-MT|`@E 99,999,999,999.99` |`MaFisRef("NF_VALFASE","MT100",M->F1_VALFASE)` ||||A|R|||
C1|F1_LOJDEST|C|2|0|Loja Dest|Loja Cliente de Destino|`@!` |`MaFisRef("NF_LOJDEST","MT100",M->F1_LOJDEST)` |||N|A|R|||
C2|F1_MENNOTA|C|60|0|Mens.p/Nota|Mensagem para Nota Fiscal|`@S45` |`texto() .Or. Vazio()` ||||||||
C3|F1_MODAL|C|2|0|Modal. trans|Modalidade de transporte|`@!` |`MaFisRef("NF_MODAL","MT100",M->F1_MODAL)` |||S|A||01=Rodoviario;02=Aereo;03=Aquaviario;04=Ferroviario;05=Dutoviario;06=Multimodal||
C4|F1_LOJAENT|C|2|0|Loja Entrega|Loja Entrega|`@!` |||||||||
C5|F1_LOJAORI|C|2|0|Lj.Cli.Orig|Loja Cliente Origem|`@!` |||||||||
C6|F1_LOJARET|C|2|0|Loja Retirad|Loja Retirada|`@!` |||||||||
C7|F1_IDNF|C|36|0|ID da NF|ID da Nota Fiscal|`@!` ||||N|A|R|||
C8|F1_FORRET|C|6|0|For Retirada|Fornecedor Retirada|`@!` |||SA2||||||
C9|F1_ESTDES|C|2|0|Estado Dest.|Estado Cliente de Destino|`@!` |`MaFisRef("NF_UFCDEST","MT100",M->F1_ESTDES)` |||S|A|R|||
D0|F1_ESTPRES|C|2|0|UF Prestacao|UF Prestacao|`@!` |`MaFisRef("NF_UFPREISS","MT100",M->F1_ESTPRES)` |||S|A|R|||
D1|F1_FIMP|C|1|0|Flag Imp NFe|Flag de impressão NF-e|`@!` ||||N|V|R|||
D2|F1_FORENT|C|6|0|For Entrega|Fornecedor Entrega|`@!` |||SA2|N|||||
D3|F1_BOMDES|C|4|0|Bombeio/Desc|NFE Bombeio/Descarga|`@!` ||||N|A|R|||
D4|F1_DEVMERC|C|1|0|Dev.merc.n.r|Devol. merc. nao recebida|`@!` |`Pertence(" SN")` |||S|A|R|S=Sim;N=Nao||
D5|F1_VALFAB|N|14|2|Vl.Fabov|Valor do Fabov|`@E 99,999,999,999.99` |`MaFisRef("NF_VALFAB","MT100",M->F1_VALFAB)` |||N|A|R|||
D6|F1_VALFAC|N|14|2|Vl.Facs|Valor do Facs|`@E 99,999,999,999.99` |`MaFisRef("NF_VALFAC","MT100",M->F1_VALFAC)` |||N|A|R|||
D7|F1_UFDESTR|C|2|0|UF Dest Tran|UF Destino do Transporte|`@!` |`Vazio() .or. (ExistCpo("SX5","12"+M->F1_UFDESTR) .And. MaFisRef("NF_UFDEST","MT100",M->F1_UFDESTR))` ||12|N|A|R|||
D8|F1_UFORITR|C|2|0|UF Ori Trans|Uf Origem do transporte|`@!` |`Vazio() .Or. (ExistCpo("SX5","12"+M->F1_UFORITR) .And. MaFisRef("NF_UFORIGEM","MT100",M->F1_UFORITR))` ||12|N|A|R|||
D9|F1_TPCOMPL|C|1|0|Tipo Compl.|Tipo de Complemento|`@!` ||||N|A|R|1=Preco; 2=Quantidade; 3=Frete||
E0|F1_SIMPNAC|C|1|0|Opt Simp Nac|Optante Simples Nacional|`@!` |`MaFisRef("NF_SIMPNAC","MT100",M->F1_SIMPNAC)` |||N|A|R|1=Sim;2=Não||
E1|F1_MOTRET|C|6|0|Codigo|Cod. Motivo do Retorno||`ExistCpo("DHI")` ||DHI||V|R|||
E2|F1_MUDESTR|C|5|0|Mun Dest Tra|Municipio Destino Transpo|`@!` |`A103MUFCTE("DEST")` ||CTEDES|N|A|R|||
E3|F1_MUORITR|C|5|0|Mun Ori Tran|Municipio Original Transp|`@!` |`A103MUFCTE("ORIG")` ||CTEORI|N|A|R|||
E4|F1_NUMAIDF|C|7|0|N. AIDF|Numero da AIDF|`@!` ||||S|A|R|||
E5|F1_RECOPI|C|1|0|Flag. RECOPI|Flag RECOPI|`@!` |||||||||
E6|F1_CLIORI|C|6|0|Cliente Orig|Cliente Origem|`@!` |||||||||
E7|F1_BASECID|N|14|2|Base Cide|Base de Calculo Cide|`@E 99,999,999,999.99` |`MaFisRef("NF_BASECID","MT100",M->F1_BASECID)` ||||||||
E8|F1_BASECPM|N|14|2|Bs.ISS CPM|Base ISS CPM|`@E 99,999,999,999.99` |`MaFisRef("NF_BASECPM","MT100",M->F1_BASECPM)` ||||||||
E9|F1_BASEFMP|N|14|2|Base FUMIPEQ|Base de Cálculo FUMIPEQ|`@E 99,999,999,999.99` |`MaFisRef("NF_BASEFMP","MT100",M->F1_BASEFMP)` ||||||||
F0|F1_BASEINA|N|14|2|Base INSS Ad|Base do INSS Condições Es|`@E 99,999,999,999.99` |`MaFisRef("NF_BASEINA","MT100",M->F1_BASEINA)` |||N|A|R|||
F1|F1_ANOAIDF|C|4|0|Ano AIDF|Ano da AIDF|`@!` ||||S|A|R|||
F2|F1_VALFET|N|14|2|Vl.Fethab|Valor do Fethab|`@E 99,999,999,999.99` |`MaFisRef("NF_VALFET","MT100",M->F1_VALFET)` |||N|A|R|||
F3|F1_VALFMD|N|14|2|Vl.Famad|Valor do Famad|`@E 99,999,999,999.99` |`MaFisRef("NF_VALFMD","MT100",M->F1_VALFMD)` |||N|A|R|||
F4|F1_VALFMP|N|14|2|Vl.FUMIPEQ|Valor do Fumipeq|`@E 99,999,999,999.99` |`MaFisRef("NF_VALFMP","MT100",M-> F1_VALFMP)` ||||||||
F5|F1_VALINA|N|14|2|Vlr INSS Ad|Valor do INSS Condições E|`@E 99,999,999,999.99` |`MaFisRef("NF_VALINA","MT100",M->F1_VALINA)` |||N|A|R|||
F6|F1_VALPEDG|N|14|2|Vlr.Pedágio|Valor Pedágio|`@E 99,999,999,999.99` |`Positivo() .And. MaFisAlt("NF_VALPEDG",M->F1_VALPEDG)` ||||||||
F7|F1_VLCIDE|N|14|2|Vl.Cide|Valor do Cide|`@E 99,999,999,999.99` |`MaFisRef("NF_VALCIDE","MT100",M->F1_VLCIDE)` ||||||||
F8|F1_VLCPM|N|14|2|Vl.ISS CPM|Valor ISS CPM|`@E 99,999,999,999.99` |`MaFisRef("NF_VALCPM","MT100",M->F1_VLCPM)` ||||||||
F9|F1_VLSENAR|N|14|2|Vl.Senar|Valor do Senar|`@E 99,999,999,999.99` |`MaFisRef("NF_VLSENAR","MT100",M->D1_VLSENAR)` ||||||||
G0|F1_VFCPANT|N|14|2|Vlr. FCP Ant|Valor do FCP Rec. Ant.|`@E 99,999,999,999.99` |`MaFisRef("NF_VFCPANT","MT100",M->F1_VFCPANT)` |||S|A|R|||
G1|F1_VEICUL1|C|8|0|Veículo 1|Código do Veoculo 1|`@!` |||DA3||A|R|||
G2|F1_VEICUL2|C|8|0|Veículo 2|Código do Veículo 2|`@!` |||DA3||A|R|||
G3|F1_VEICUL3|C|8|0|Veículo 3|Código do Veículo 3|`@!` |||DA3||A|R|||
G4|F1_VERBAFO|C|9|0|Verba Folha|Verba da Folha|||||S|||||
G5|F1_BASCOFI|N|14|2|Base COFINS|Base COFINS|`@E 99,999,999,999.99` |`MaFisRef("NF_BASECOF","MT100",M->F1_BASCOFI)` ||||||||
G6|F1_BASCSLL|N|14|2|Base CSLL|Base CSLL|`@E 99,999,999,999.99` |`MaFisRef("NF_BASECSL","MT100",M->F1_BASCSLL)` ||||||||
G7|F1_BASFECP|N|14|2|Base FCP Pr.|Base FCP Próprio|`@E 99,999,999,999.99` |`MaFisRef("NF_BASFECP","MT100",M->F1_BASFECP)` |||S|A|R|||
G8|F1_BASEFUN|N|14|2|Bas.FUNRURAL|Base Calculo FUNRURAL|`@E 99,999,999,999.99` |`MaFisRef("NF_BASEFUN","MT100",M->F1_BASEFUN)` |||N|A|R|||
G9|F1_CODRGS|C|1|0|Status RGS|Status registro saida|||||N|A|R|||
H0|F1_CODROM|C|10|0|Romaneio|Código do Romaneio|`@!` ||||N|A|R|||
H1|F1_BSFCCMP|N|14|2|Base FCP Cmp|Base FCP Complementar|`@E 99,999,999,999.99` |`MaFisRef("NF_BSFCCMP","MT100",M->F1_BSFCCMP)` |||S|A|R|||
H2|F1_BSFCPST|N|14|2|Base FCP ST|Base FCP ST|`@E 99,999,999,999.99` |`MaFisRef("NF_BSFCPST","MT100",M->F1_BSFCPST)` |||S|A|R|||
H3|F1_BASPIS|N|14|2|Base PIS|Base do PIS|`@E 99,999,999,999.99` |`MaFisRef("NF_BASEPIS","MT100",M->F1_BASPIS)` ||||||||
H4|F1_BFCPANT|N|14|2|Base FCP Ant|Base FCP Rec. Ant.|`@E 99,999,999,999.99` |`MaFisRef("NF_BFCPANT","MT100",M->F1_BFCPANT)` |||S|A|R|||
H5|F1_QTDCONF|N|2|0|Qtd conferen|Qtd de conferentes|`99` ||||N|A|R|||
H6|F1_NUMMDF|C|9|0|Numero MDFe|Numero do MDFe vinculado|`@!` ||||S|A|R|||
H7|F1_MSIDENT|C|10|0|Ident.Reg.|Ident.Reg.|||||N|V|R|||
H8|F1_STATCON|C|1|0|Stat conf|Status da conf. fisica|||||N|A|R|0=Nao Conferido;1=Conferido;2=Divergente;3=Em Conferencia||
H9|F1_SERMDF|C|3|0|Serie MDFe|Serie do MDFe vinculado|`@!` ||||S|A|R|||
I0|F1_SDOC|C|3|0|Série Doc.|Série do Documento Fiscal|`!!!` ||||N|V|R|||
I1|F1_SDOCMAN|C|3|0|Série Manual|Série Doc. Manual|`!!!` ||||N|V|R|||
I2|F1_SDOCORI|C|3|0|Sér.despesa|Série do Docto.de Despesa|`!!!` ||||N|V|R|||
I3|F1_TPCTE|C|1|0|Tipo de CT-e|Indica tipo de CT-e|`@!` |`Pertence(" NCAS")` |||S|A|R|N=Normal;C=Complem.Valores;A=Anula.Valores;S=Substituto||
I4|F1_TPFRETE|C|1|0|Tipo de fret|Indica tipo de frete|`@!` ||||S|A|R|||
I5|F1_DAUTNFE|D|8|0|Data de Auto|Data de Autorizacao da NF|||||N|A|R|||
I6|F1_DOCFOL|C|9|0|Doc.Folha|Documento da Folha|||||S|||||
I7|F1_DTCPISS|D|8|0|Dt. Comp ISS|Desc. Data Competencia||||||||||
I8|F1_FLAGRGS|C|4|0|Flag RGS|Flag registro de saída|||||N|A|R|||
I9|F1_EVENFLG|C|1|0|Flag CCe|Flag da carta de correcao|||||N|A|R|||
J0|F1_HAUTNFE|C|5|0|Hora de Auto|Hora de Autorizacao da NF|||||N|A|R|||
J1|F1_HISTRET|M|10|0|Historico|Historico do Retorno||||||A|R|||
J2|F1_IDRECOP|C|6|0|Id Recopi|ID Solicitação RECOPI|`@!` ||||N|V|R|||
J3|F1_IDRGS|C|54|0|Id RGS|Id do registro de saída|||||N|A|R|||
J4|F1_IDSA1|C|20|0|ID Hist. SA1|ID Hist. SA1|`@!` |`MaFisRef("NF_IDSA1","MT100",M->F1_IDSA1)` |||N||R|||
J5|F1_IDSA2|C|20|0|ID Hist. SA2|ID Hist. SA2|`@!` |`MaFisRef("NF_IDSA2","MT100",M->F1_IDSA2)` |||N||R|||
J6|F1_IDSED|C|20|0|ID Hist. SED|ID Hist. SED|`@!` |`MaFisRef("NF_IDSED","MT100",M->F1_IDSED)` |||N||R|||
J7|F1_IDCCE|C|54|0|Id CC-e|Id da CC-e|||||N|A|R|||
J8|F1_MENPAD|C|3|0|Mens.Padrao|Mensagem Padrao 1|`@!` |`vazio() .or. existcpo("SM4")` ||SM4||||||
J9|F1_INCISS|C|5|0|Mun. Incid.|Munic. de Incid. do ISS|`@99999` |||CC2||||||


## SIX - Índices da tabela

ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|F1_FILIAL+F1_DOC+F1_SERIE+F1_FORNECE+F1_LOJA+F1_TIPO|Numero + Serie + Fornecedor + Loja + Tipo da Nota|XXX+XXX+SA2||S|
2|F1_FILIAL+F1_FORNECE+F1_LOJA+F1_DOC|Fornecedor + Loja + Numero|SA2||S|
3|F1_FILIAL+F1_REMITO|N§ Remito|||S|
4|F1_FILIAL+F1_ORDPAGO|Ordem Pagto|||S|
5|F1_FILIAL+F1_HAWB+F1_TIPO_NF+F1_DOC+F1_SERIE|No. Conhec. + Tipo Docto. + Numero + Serie|||S|
6|F1_FILIAL+F1_NFELETR+DTOS(F1_EMINFE)+F1_FORNECE+F1_LOJA|NF Eletr. + Emissão NF-e + Fornecedor + Loja|XXX+XXX+SA2||S|
7|F1_FILIAL+F1_NODIA|Seq. Diário|||S|
8|F1_FILIAL+F1_CHVNFE|Chave NFe|||S|
A|F1_FILIAL+F1_DOC+F1_SDOC+F1_FORNECE+F1_LOJA+F1_TIPO|Numero + Série Doc. + Fornecedor + Loja + Tipo da Nota|||N|
B|F1_FILIAL+F1_HAWB+F1_TIPO_NF+F1_DOC+F1_SDOC|No. Conhec. + Tipo Docto. + Numero + Série Doc.|||N|
D|F1_FILIAL+F1_IDNF|ID da NF|||S|


