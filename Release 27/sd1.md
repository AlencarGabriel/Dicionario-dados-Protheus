# SD1 - Itens das NF de Entrada
## SX3 - Campos da tabela

X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|D1_FILIAL|C|2|0|Filial|Filial do Sistema|||||N|||||
02|D1_LEGENDA|C|13|0|Legenda|Legenda|`@BMPS2` |||||V|V|||
03|D1_ITEM|C|4|0|Item NF|Item da Nota Fiscal|`@!` |`.F.` |||N|V||||
04|D1_COD|C|15|0|Produto|Codigo do Produto|`@!` |`Vazio().or.(A093Prod().And.A103PrdGrd().And.MaFisRef("IT_PRODUTO","MT100",M->D1_COD))` ||SB1|S|||||
05|D1_UM|C|2|0|Unidade|Unidade de Medida||`ExistCpo("SAH")` ||SAH|S|V||||
06|D1_SEGUM|C|2|0|Segunda UM|Segunda Unidade de Medida||`Vazio() .Or. ExistCpo("SAH")` ||SAH|S|V||||
07|D1_QUANT|N|11|2|Quantidade|Quantidade do Produto|`@E 99999999.99` |`A140DespGat() .And.  A103TOLER().And.A100SegUm().And.MaFisRef("IT_QUANT","MT100",M->D1_QUANT)` |||S|||||
08|D1_VUNIT|N|14|2|Vlr.Unitario|Valor Unitario|`@E 99,999,999,999.99` |`A103TOLER().And.MaFisRef("IT_PRCUNI","MT100",M->D1_VUNIT)` |||S|||||
09|D1_TOTAL|N|14|2|Vlr.Total|Valor Total|`@E 99,999,999,999.99` |`A103Total(M->D1_TOTAL) .and. MaFisRef("IT_VALMERC","MT100",M->D1_TOTAL) .And. MTA103TROP(n)` |||N|||||
10|D1_VALIPI|N|14|2|Vlr.IPI|Valor do IPI do Item|`@E 999,999,999.99` |`MaFisRef("IT_VALIPI","MT100",M->D1_VALIPI)` |||N|||||
11|D1_VLSLXML|N|14|2|ICMS ST For.|ICMS ST Fornecedor|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("IT_VLSLXML","MT100",M->D1_VLSLXML)` ||||A|R|||
12|D1_VALICM|N|14|2|Vlr.ICMS|Valor do ICM do Item|`@E 999,999,999.99` |`MaFisRef("IT_VALICM","MT100",M->D1_VALICM)` |||N|||||
13|D1_OPER|C|2|0|Tp.Oper|Tipo de Operacao||`ExistCpo("SX5","DJ"+M->D1_OPER)  .And. MTA103TROP(n) .And. MaFisRef("IT_TPOPER","MT100",M->D1_OPER)` ||DJ|||V|||
14|D1_TES|C|3|0|Tipo Entrada|Tipo de entrada da nota|`@9` |`Existcpo("SF4").And.MaAvalTes("E",M->D1_TES).And.MaFisRef("IT_TES","MT100",M->D1_TES)` ||SF4|N|||||
15|D1_CF|C|5|0|Cod. Fiscal|Codigo Fiscal da Operacao|`@9` |`NaoVazio().and.AvalCfo("SD1",M->D1_CF).and.MaFisRef("IT_CF","MT100",M->D1_CF)` ||13|N|||||
16|D1_DESC|N|5|2|Desc.Item|Desconto no Item|`@E 99.99` ||||N||||`A103VLDDSC()` |
17|D1_IPI|N|6|2|Aliq. IPI|Alíquota de IPI|`@E 99.99` |`MaFisRef("IT_ALIQIPI","MT100",M->D1_IPI)` |||N|||||
18|D1_PICM|N|5|2|Aliq. ICMS|Alíquota de ICMS|`@E 99.99` |`VldAliqIcm(M->D1_PICM).And.MaFisRef("IT_ALIQICM","MT100",M->D1_PICM)` |||N|||||
19|D1_PESO|N|10|3|Peso total|Peso do produto rateio|`@E 999999.999` |`MaFisRef("IT_PESO","MT100",M->D1_PESO)` |||N|||||
20|D1_CONTA|C|20|0|C Contabil|Codigo da Conta Contabil|`@!` |`(Vazio().or. Ctb105Cta()) .And. A103VldCC()` ||CT1|N|||||
21|D1_ITEMCTA|C|9|0|Item Conta|Item da Conta Contabil|`@!` |`(Vazio().Or.Ctb105Item()) .And. A103VldCC()` ||CTD|N|||||
22|D1_CC|C|9|0|Centro Custo|Centro de Custo|`@!` |`(Vazio() .or. Ctb105CC()) .And.A103VldCC()` ||CTT|N|||||
23|D1_OP|C|14|0|Ord Producao|Ordem de Producao|`@9` |`A103VldOP()` ||SC2|N|||||
24|D1_PEDIDO|C|6|0|No do Pedido|pedido de compra/venda|`@!` |`vazio().or. (existcpo("SC7", M->D1_PEDIDO,1).And.A103PC())` ||SC7|N|V||||
25|D1_ITEMPC|C|4|0|Item do Ped.|Item do ped.compra/venda|`@!` |`A103Item()` |||N|V||||
26|D1_FORNECE|C|6|0|Forn/Cliente|Codigo do Forn/Cliente|`@!` ||||N|||||
27|D1_LOJA|C|2|0|Loja|Loja do Forn/Cliente|`@!` ||||N|||||
28|D1_LOCAL|C|2|0|Armazem|Codigo do Armazem|`@!` |`ExistCpo("NNR") .And. A100Local()` ||NNR|N|||||
29|D1_DOC|C|9|0|Documento|Numero do Documento/Nota|`@!` ||||N|||||
30|D1_EMISSAO|D|8|0|DT Emissao|Data de Emissao|||ddatabase||N|||||
31|D1_DTDIGIT|D|8|0|DT Digitacao|Data de Digitacao|||ddatabase||N|||||
32|D1_GRUPO|C|4|0|Grupo|Grupo do Produto|`@!` |||SBM|N|||||
33|D1_TIPO|C|1|0|Tipo Docto.|Tipo do Documento|`!` |`pertence("NCTOB")` |||N|||||
34|D1_SERIE|C|3|0|Serie|Serie da Nota Fiscal|`!!!` ||||N|||||
35|D1_CUSTO2|N|14|2|Custo Moeda2|Custo de Entrada Moeda 2|`@E 999,999,999.99` ||||N|||||
36|D1_CUSTO3|N|14|2|Custo Moeda3|Custo de Entrada Moeda 3|`@E 999,999,999.99` ||||N|||||
37|D1_CUSTO4|N|14|2|Custo Moeda4|Custo de Entrada Moeda 4|`@E 999,999,999.99` ||||N|||||
38|D1_CUSTO5|N|14|2|Custo Moeda5|Custo de Entrada Moeda 5|`@E 999,999,999.99` ||||N|||||
39|D1_TP|C|2|0|Tipo Produto|Tipo do Produto Vendido|`@!` ||||N|||||
40|D1_QTSEGUM|N|11|2|Qtde 2a UM|Segunda Unidade de Medida|`@E 99,999,999.99` |`A100SegUm().and.positivo().or.vazio()` |||N|||||
41|D1_NUMSEQ|C|6|0|Num.Sequenc.|Numeracao sequencial|`@!` ||||N|||||
42|D1_DATACUS|D|8|0|DT Custo|Data do Custo a Vista|||ddatabase||N|||||
43|D1_NFORI|C|9|0|Docto. Orig.|Documento Original|`@!` |`IIF(cTipo=="D",NaoVazio(),.T.) .And. MaFisRef("IT_NFORI","MT100",M->D1_NFORI)` |||N|||||
44|D1_SERIORI|C|3|0|Serie Orig.|Serie do Doc. Original|`!!!` |`MaFisRef("IT_SERORI","MT100",M->D1_SERIORI)` |||N|||||
45|D1_ITEMORI|C|4|0|It.Doc Orig.|Item do Docto. de Origem|`@!` |`A103ITDEV(M->D1_ITEMORI)` |||N|||||
46|D1_QTDEDEV|N|11|2|Qtde Devol.|Qtde Devolvida|`@E 99,999,999.99` ||||N|||||
47|D1_VALDEV|N|14|2|Valor Devol.|Valor Devolvido|`@E 9,999,999,999.99` ||||N|||||
48|D1_ORIGLAN|C|2|0|Orig. Lancto|Origem do Lancamento|`@!` ||||N|||||
49|D1_ICMSRET|N|14|2|ICMS Solid.|Valor do ICMS Solidario|`@E 99,999,999,999.99` |`MaFisRef("IT_VALSOL","MT100",M->D1_ICMSRET)` ||||||||
50|D1_BRICMS|N|14|2|Ret. ICMS|Base de Retencao ICMS|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("IT_BASESOL","MT100",M->D1_BRICMS)` ||||||||
51|D1_NUMCQ|C|6|0|Numero do CQ|Num. Controle Qualidade|||||N|V||||
52|D1_DATORI|D|8|0|Data da NF O|Data Emissao NF Original||||||||||
53|D1_BASEICM|N|14|2|Base Icms|Valor Base do Icms|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEICM","MT100",M->D1_BASEICM)` |||N|||||
54|D1_VALDESC|N|12|2|Desconto|Valor do Desconto no Item|`@E 999,999,999.99` |`MaFisRef("IT_DESCONTO","MT100",M->D1_VALDESC)` |||N||||`A103VLDDSC()` |
55|D1_IDENTB6|C|6|0|Ident. PD3|Identificador no Poder 3|||||N|V||||
56|D1_LOTEFOR|C|18|0|Lote Fornec.|N·m.do Lote no Fornecedor|||||N|||||
57|D1_SKIPLOT|C|1|0|Skip Lote|Controle do Skip Lote|||||N|||||
58|D1_BASEIPI|N|14|2|Vlr.Base IPI|Valor Base de Calc. IPI|`@E 999,999,999,999.99` |`MaFisRef("IT_BASEIPI","MT100",M->D1_BASEIPI)` |||N|||||
59|D1_SEQCALC|C|14|0|Seq.Recalc.|Seq.Recalc.Custo Médio||||||||||
60|D1_LOTECTL|C|10|0|Lote|Lote||`A103LotCTL()` |||N|||||
61|D1_NUMLOTE|C|6|0|Sub-Lote|Sub-Lote|`@!` |`A103Zera() .And. A103LotCTL()` ||||||||
62|D1_DTVALID|D|8|0|Valid. Lote|Validade do Lote inform.||`A103DtVld(M->D1_DTVALID)` |CTOD("  /  /  ")||N|||||
63|D1_PLACA|C|7|0|Placa|Placa do Veiculo|`@R XXX 9999` ||||N|||||
64|D1_CHASSI|C|25|0|Chassi|Codigo do Chassi|`@!` ||||S|||||
65|D1_ANOFAB|C|2|0|Ano|Ano de Fabricacao|`99` |`NaoVazio()` |||N|||||
66|D1_MODFAB|C|2|0|Mod|Modelo de Fabricacao|`99` |`NaoVazio()` |||N|||||
67|D1_MODELO|C|15|0|Modelo|Modelo|`@!` |`texto()` |||N|||||
68|D1_COMBUST|C|10|0|Combustivel|Tipo de Combustivel|`@!` |`Combust()` |||N|||||
69|D1_COR|C|3|0|Cor|Cor Predominante|`@!` ||||N|||||
70|D1_EQUIPS|C|3|0|Equipamentos|Equipamentos adicionais|`@!` |`Pertence("S¦N")` |||N|||||
71|D1_FORMUL|C|1|0|Form. Prop.|Formulario Proprio|`!` ||||N|||||
72|D1_II|N|14|2|Vlr.I.I.|Vlr. Imposto Importacao|`@E 99,999,999,999.99` |`MaFisRef("IT_VALII","MT100",M->D1_II)` |||N|A|R|||
73|D1_TEC|C|16|0|TEC/NCM/QUAL|TEC + NCM + QUALIFICADOR|||||N|V||||
74|D1_CONHEC|C|20|0|Num. Conhec.|Numero Conhec Importacao|`@!` ||||N|||||
75|D1_GERAPV|C|1|0|Gera PV|Gera Pedido de Venda|`@!` |`Pertence("SN") .And. a100VerPv()` |||N||V|S=Sim;N=Nõo||
76|D1_NUMPV|C|6|0|Numero do PV|Numero do Pedido de Venda|||||N|V||||
77|D1_ITEMPV|C|2|0|Item do PV|Item do Pedido de Venda|||||N|V||||
78|D1_CUSFF1|N|14|2|Custo FIFO 1|Custo FIFO Moeda 1|`@E 999,999,999.99` ||||N|||||
79|D1_CUSFF2|N|14|2|Custo FIFO 2|Custo FIFO Moeda 2|`@E 999,999,999.99` ||||N|||||
80|D1_CUSFF3|N|14|2|Custo FIFO 3|Custo FIFO Moeda 3|`@E 999,999,999.99` ||||N|||||
81|D1_CUSFF4|N|14|2|Custo FIFO 4|Custo FIFO Moeda 4|`@E 999,999,999.99` ||||N|||||
82|D1_CUSFF5|N|14|2|Custo FIFO 5|Custo FIFO Moeda 5|`@E 999,999,999.99` ||||N|||||
83|D1_CODCIAP|C|6|0|Codigo CIAP|Codigo CIAP|`@!` ||||N|V|||`.F.` |
84|D1_CLASFIS|C|3|0|Sit.Tribut.|Situacao Tributaria|`@!` |`MAFISREF("IT_CLASFIS","MT100",M->D1_CLASFIS)` |||N|||||
85|D1_BASIMP1|N|14|2|Base Imp. 1|Base de Calculo Imposto 1|`@E  99,999,999,999.99` |`MaFisRef("IT_BASEIV1","MT100",M->D1_BASIMP1)` |||N|||||
86|D1_REMITO|C|9|0|Remito|Remito|`@!` |`MAFISREF("IT_REMITO","MT100",M->D1_REMITO)` ||||V||||
87|D1_SERIREM|C|3|0|Serie remito|Serie remito|`!!!` |||||V||||
88|D1_CUSTO|N|14|2|Custo Moeda1|Custo de Entrada Moeda 1|`@E 999,999,999.99` ||||N|||||
89|D1_BASIMP3|N|14|2|Base Imp. 3|Base de Calculo Imposto 3|`@E  99,999,999,999.99` |`MaFisRef("IT_BASEIV3","MT100",M->D1_BASIMP3)` |||N|||||
90|D1_BASIMP4|N|14|2|Base Imp. 4|Base de Calculo Imposto 4|`@E  99,999,999,999.99` |`MaFisRef("IT_BASEIV4","MT100",M->D1_BASIMP4)` |||N|||||
91|D1_BASIMP5|N|14|2|Base Imp. 5|Base de Calculo Imposto 5|`@E  99,999,999,999.99` |`MaFisRef("IT_BASECF2","MT100",M->D1_BASIMP5)` |||N|||||
92|D1_BASIMP6|N|14|2|Base Imp. 6|Base de Calculo Imposto 6|`@E  99,999,999,999.99` |`MaFisRef("IT_BASEPS2","MT100",M->D1_BASIMP6)` |||N|||||
93|D1_VALIMP1|N|14|2|Valor Imp. 1|Valor do Imposto 1|`@E  99,999,999,999.99` |`MaFisRef("IT_VALIV1","MT100",M->D1_VALIMP1)` |||N|||||
94|D1_VALIMP2|N|14|2|Valor Imp. 2|Valor do Imposto 2|`@E  99,999,999,999.99` |`MaFisRef("IT_VALIV2","MT100",M->D1_VALIMP2)` |||N|||||
95|D1_VALIMP3|N|14|2|Valor Imp. 3|Valor do Imposto 3|`@E  99,999,999,999.99` |`MaFisRef("IT_VALIV3","MT100",M->D1_VALIMP3)` |||N|||||
96|D1_VALIMP4|N|14|2|Valor Imp. 4|Valor do Imposto 4|`@E  99,999,999,999.99` |`MaFisRef("IT_VALIV4","MT100",M->D1_VALIMP4)` |||N|||||
97|D1_VALIMP5|N|14|2|Valor Imp. 5|Valor do Imposto 5|`@E  99,999,999,999.99` |`MaFisRef("IT_VALCF2","MT100",M->D1_VALIMP5)` |||N|||||
98|D1_VALIMP6|N|14|2|Valor Imp. 6|Valor do Imposto 6|`@E  99,999,999,999.99` |`MaFisRef("IT_VALPS2","MT100",M->D1_VALIMP6)` |||N|||||
99|D1_CBASEAF|C|14|0|Imobilizado|Numero do Imobilizado|`@!` ||||N|||||
A0|D1_ICMSCOM|N|14|2|ICMS Comple.|Valor ICMS Complementar|`@E 99,999,999,999.99` |`MaFisRef("IT_VALCMP","MT100",M->D1_ICMSCOM)` |||N|V||||
A1|D1_CIF|N|15|2|C.I.F.|C.I.F.|`@E 999,999,999,999.99` ||||N|||||
A2|D1_ITEMREM|C|4|0|Item remito|Item remito||||||V||||
A3|D1_PROJ|C|10|0|Cod. Proj.|Código do Projeto|`@!` |`Vazio().Or.ExistCpo("AF8")` |||S|A|R|||
A4|D1_BASIMP2|N|14|2|Base Imp. 2|Base de Calculo Imposto 2|`@E  99,999,999,999.99` |`MaFisRef("IT_BASEIV2","MT100",M->D1_BASIMP2)` |||N|||||
A5|D1_TIPO_NF|C|1|0|Tipo Docto.|Tipo Doc. - Importacao|||||N|||||
A6|D1_ALQIMP1|N|6|2|Aliq. Imp. 1|Aliquota do Imposto 1|`@E  999.99` |`MaFisRef("IT_ALIQIV1","MT100",M->D1_ALQIMP1)` |||N|||||
A7|D1_ALQIMP2|N|6|2|Aliq. Imp. 2|Aliquota do Imposto 2|`@E  999.99` |`MaFisRef("IT_ALIQIV2","MT100",M->D1_ALQIMP2)` ||||||||
A8|D1_ALQIMP3|N|6|2|Aliq. Imp. 3|Aliquota do Imposto 3|`@E  999.99` |`MaFisRef("IT_ALIQIV3","MT100",M->D1_ALQIMP3)` ||||||||
A9|D1_ALQIMP4|N|6|2|Aliq. Imp. 4|Aliquota do Imposto 4|`@E  999.99` |`MaFisRef("IT_ALIQIV4","MT100",M->D1_ALQIMP4)` ||||||||
B0|D1_ALQIMP5|N|6|2|Aliq. Imp. 5|Aliquota do Imposto 5|`@E  999.99` |`MaFisRef("IT_ALIQCF2","MT100",M->D1_ALQIMP5)` ||||||||
B1|D1_ALQIMP6|N|6|2|Aliq. Imp. 6|Aliquota do Imposto 6|`@E  999.99` |`MaFisRef("IT_ALIQPS2","MT100",M->D1_ALQIMP6)` ||||||||
B2|D1_QTDPEDI|N|11|2|Qtde Pedido|Qtde em Pedido de Compras|`@E 99,999,999.99` ||||N|||||
B3|D1_VALFRE|N|14|2|Vlr. Frete|Valor do Frete|`@E 99,999,999,999.99` |`A140DespGat() .And. MaFisRef("IT_FRETE","MT100",M->D1_VALFRE)` |||N|||||
B4|D1_ALIIMA|N|5|2|Aliq. IMA-MT|Alíquota do IMA-MT|`@E 99.99` |`MaFisRef("IT_ALIIMA","MT100",M->D1_ALIIMA)` ||||A|R|||
B5|D1_RATEIO|C|1|0|Rateio|Possui Rateio por CC|`@!` |`Pertence("12 ").And.A103RatCC(M->D1_RATEIO)` |"2"||N|||1=Sim;2=Nao||
B6|D1_SEGURO|N|14|2|Vlr. Seguro|Valor do Seguro do item|`@E 99,999,999,999.99` |`MaFisRef("IT_SEGURO","MT100",M->D1_SEGURO)` |||N|||||
B7|D1_DESPESA|N|14|2|Vlr. Despesa|Valor das Despesas|`@E 99,999,999,999.99` |`MaFisRef("IT_DESPESA","MT100",M->D1_DESPESA)` |||N|||||
B8|D1_BASEIRR|N|14|2|Base de IRRF|Base de calculo do IRRF|`@E 99,999,999.99` |`MaFisRef("IT_BASEIRR","MT100",M->D1_BASEIRR)` |||N|||||
B9|D1_ALIQIRR|N|5|2|Aliq. IRRF|Aliquota de IRRF|`@E 999.99` |`MafisRef("IT_ALIQIRR","MT100",M->D1_ALIQIRR)` |||N|||||
C0|D1_VALIRR|N|14|2|Valor IRRF|Valor do IRRF|`@E 999,999,999.99` |`MaFisRef("IT_VALIRR","MT100",M->D1_VALIRR)` |||N|||||
C1|D1_BASEISS|N|14|2|Base de ISS|Base de calculo do ISS|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEISS","MT100",M->D1_BASEISS)` |||N|||||
C2|D1_ALIQISS|N|5|2|Aliq. ISS|Aliquota de ISS|`@E 99.99` |`MaFisRef("IT_ALIQISS","MT100",M->D1_ALIQISS)` |||N|||||
C3|D1_VALISS|N|14|2|Valor do ISS|Valor do ISS|`@E 99,999,999,999.99` |`MaFisRef("IT_VALISS","MT100",M->D1_VALISS)` |||N|||||
C4|D1_BASEINS|N|14|2|Base de INSS|Base de calculo do INSS|`@E 999,999,999.99` |`MaFisRef("IT_BASEINS","MT100",M->D1_BASEINS)` |||N|||||
C5|D1_ALIQINS|N|5|2|Aliq. INSS|Aliquota de INSS|`@E 99.99` |`MaFisRef("IT_ALIQINS","MT100",M->D1_ALIQINS)` |||N|||||
C6|D1_VALINS|N|14|2|Vlr. do INSS|Valor do INSS|`@E 999,999,999.99` |`MaFisRef("IT_VALINS","MT100",M->D1_VALINS)` |||N|||||
C7|D1_CUSORI|N|16|3|Custo Orig.1|Custo Original Moeda 1|`@E 999,999,999,999.999` |||||||||
C8|D1_LOCPAD|C|6|0|Local Exter.|Local Externo Carga/Desc.|`@!` |`If(IntDL(),ExistCpo('DC9'),Vazio().Or.ExistCpo('DC9'))` ||DC9|S|||||
C9|D1_CLVL|C|9|0|Classe Valor|Classe Valor Contabil|`@!` |`(Vazio().Or. Ctb105ClVl()) .And. A103VldCC()` ||CTH|N||||`CtbInUse()` |
D0|D1_ORDEM|C|6|0|Ordem Servic|Ordem de Servico|`@!` |`(Empty() .Or. EXISTCPO("STJ",M->D1_ORDEM)) .And. NGSDCHKORDEM(M->D1_ORDEM)` ||NGJ|S|||||
D1|D1_CODFIS|C|15|0|Cod.Fis.Forn|Código Fiscal Fornecedor|`@!` |`Vazio() .Or. Mt060VldFis(M->D1_CODFIS,cA100For,cLoja)` |||N|A|R|||
D2|D1_CNO|C|14|0|Numero CNO|Numero do CNO||||SON|N|A|R|||
D3|D1_ORDDIA|C|4|0|Ordem na DIA|Ordem na DIA|`@!` ||||S|A|R|||
D4|D1_NRECAGR|C|5|0|Num Rec Agro|Num Receita Agronômica|`@!` ||||N|A|R|||
D5|D1_VALFASE|N|14|2|Vlr.FASE-MT|Valor do FASE|`@E 99,999,999,999.99` |`MaFisRef("IT_VALFASE","MT100",M->D1_VALFASE)` ||||A|R|||
D6|D1_TESDES|C|3|0|Tipo Entrada|Tes Entrada de Destino|`@9` ||||N|||||
D7|D1_VFCPDIF|N|14|2|Valor FECP|FECP da UF de destino|`@E 99,999,999,999.99` |`MaFisRef("IT_VFCPDIF","MT100",M->D1_VFCPDIF)` |||N|A|R|||
D8|D1_PDDES|N|6|2|Perc. Destin|Perc. Difal Destino|`@E 999.99` |`MaFisRef("IT_PDDES","MT100",M->D1_PDDES)` |||N|A|R|||
D9|D1_PERCINP|N|5|2|Perc.INSS.Pt|Percent. do INSS Patronal|`@E 99.99` |`Positivo() .And. MaFisRef("IT_PERCINP","MT100",M->D1_PERCINP)` |||N|A|R|||
E0|D1_FILEDT|C|2|0|Fil Edital|Filial Edital|||||N|V|R|||
E1|D1_BASFUND|N|14|2|Base FUNDESA|Base do FUNDESA|`@E 99,999,999,999.99` |`MaFisRef("IT_BASFUND","MT100",M->D1_BASFUND)` ||||A|R|||
E2|D1_BASIMA|N|14|2|Base IMA-MT|Base do IMA-MT|`@E 99,999,999,999.99` |`MaFisRef("IT_BASIMA","MT100",M->D1_BASIMA)` ||||A|R|||
E3|D1_BASFASE|N|14|2|Base FASE-MT|Base do FASE-MT|`@E 99,999,999,999.99` |`MaFisRef("IT_BASFASE","MT100",M->D1_BASFASE)` ||||A|R|||
E4|D1_BASEDES|N|14|2|Base. Destin|Base. Difal Destino|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEDES","MT100",M->D1_BASEDES)` |||N|A|R|||
E5|D1_ALIFASE|N|5|2|Aliq.FASE-MT|Alíquota do FASE-MT|`@E 99.99` |`MaFisRef("IT_ALIFASE","MT100",M->D1_ALIFASE)` ||||A|R|||
E6|D1_ALIFUND|N|5|2|Aliq.FUNDESA|Alíquota do FUNDESA|`@E 99.99` |`MaFisRef("IT_ALIFUND","MT100",M->D1_ALIFUND)` ||||A|R|||
E7|D1_CODGRP|C|4|0|Grupo|Grupo Veiculos/Oficina|`@!!!!` |`VldAuxCod1("D1_CODGRP","D1_CODITE")` |IniAuxCod(SD1->D1_COD,"D1_CODGRP")|SBM|S||V|||
E8|D1_CODITE|C|27|0|Cod.Produto|Produto Veiculos/Oficina||`VldAuxCod2("D1_COD","D1_CODGRP")` |IniAuxCod(SD1->D1_COD,"D1_CODITE")|B00|S||V|||
E9|D1_SERVIC|C|3|0|Cod.Servico|Codigo do Servico|`@!` |`Vazio().Or.ExistCpo('DC5')` ||DC5|S|||||
F0|D1_STSERV|C|1|0|Status Serv.|Status do Servico|`@!` |`Pertence('123')` |'1'||N|V||1=Servico Nao Executado;2=Servico Interrompido;3=Servico Executado||
F1|D1_ENDER|C|15|0|Endereco Ini|Endereco Inicial|`@!` |`If(IntDl(),ExistCpo('SBE', M->D1_ENDER, 9),Vazio().Or.ExistCpo('SBE', M->D1_ENDER, 9))` ||SBE|S|||||
F2|D1_TPESTR|C|6|0|Estr.Fisica|Cod. da Estrutura Fisica|`@!` |`If(IntDl(),ExistCpo("DC8"),Vazio().Or.ExistCpo("DC8"))` ||DC8|S|||||
F3|D1_DESEST|C|20|0|Dsc.Est.Fis.|Dsc.Estrutura Fisica|`@!` ||If(Inclui,"",Posicione("DC8",1,xFilial("DC8")+SD1->D1_TPESTR,"DC8_DESEST"))||S|V|V|||
F4|D1_PDORI|N|6|2|Perc. Origem|Perc. Difal Origem|`@E 999.99` |`MaFisRef("IT_PDORI","MT100",M->D1_PDORI)` |||N|A|R|||
F5|D1_PCCENTR|C|6|0|Ped.Centr|Pedido Centralizador|`@!` |`A178Valid()` ||||||||
F6|D1_QTPCCEN|N|11|2|Qt.Vinc.PCC.|Qt.Vinc.Ped.Compra Centr|`@E 99999999.99` |||||||||
F7|D1_ITPCCEN|C|4|0|It.Pc.Cent|It.Pedido Centralizador|`@!` |`A178Valid()` ||||||||
F8|D1_ALIQCMP|N|6|2|Aliq Comp|Aliq. ICMS complementar|`@E 999.99` |`MaFisRef("IT_ALIQCMP","MT100",M->D1_ALIQCMP)` |||N|A|R|||
F9|D1_REGWMS|C|1|0|Regra WMS|Regra de apanhe do WMS|`9` |`Pertence("123")` ||||||1=Lote;2=Numero de Serie;3=Data||
G0|D1_VALFUND|N|14|2|Vlr.FUNDESA|Valor do FUNDESA|`@E 99,999,999,999.99` |`MaFisRef("IT_VALFUND","MT100",M->D1_VALFUND)` ||||A|R|||
G1|D1_VALINP|N|14|2|Val.INSS.Pt|Valor do INSS Patronal|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("IT_VALINP","MT100",M->D1_VALINP)` |||N|A|R|||
G2|D1_VRDICMS|N|16|2|Val.Desc.ICM|Valor de Redução Desc.ICM|`@E 9,999,999,999,999.99` |`MaFisRef("IT_VRDICMS","MT100",M->D1_VRDICMS)` |||N|A|R|||
G3|D1_TIPODOC|C|2|0|Id. Doc.|Identificador de doc.|||||N|||||
G4|D1_POTENCI|N|6|2|Potencia Lot|Potencia do Lote|`@E 999.99` |`A103Potenc()` |||N|||||
G5|D1_TRT|C|3|0|Seq.Estrut.|Sequencia na Estrutura|`@!` |||||||||
G6|D1_TESACLA|C|3|0|TES Selecion|TES para Classificacäo|||||N|V|R|||
G7|D1_NUMDESP|C|16|0|Num Despacho|Numero do Despacho|`@!` |||||||||
G8|D1_ORIGEM|C|3|0|Origem Imp.|Origem da Importacäo|`@!` |||||||||
G9|D1_GRADE|C|1|0|Grade|Referencia de Grade?|`@!` |`Pertence("SN")` ||||V|R|S=Sim;N=Nao||
H0|D1_ITEMGRD|C|3|0|Item Grade|Item Grade|`@!` |||||V|R|||
H1|D1_DESCICM|N|14|2|Desc. ICMS|Desconto ICMS|`@E 999,999,999.99` |`MaFisRef("IT_DEDICM","MT100",M->D1_DESCICM)` |||S|A|R|||
H2|D1_VALIMA|N|14|2|Vlr. IMA-MT|Valor do IMA-MT|`@E 99,999,999,999.99` |`MaFisRef("IT_VALIMA","MT100",M->D1_VALIMA)` ||||A|R|||
H3|D1_VALFMP|N|14|2|Vl. FUMIPEQ|Valor do FUMIPEQ|`@E 99,999,999,999.99` |`MaFisRef("IT_VALFMP","MT100",M->D1_VALFMP)` ||||||||
H4|D1_VALFEEF|N|14|2|Val.FEEF.RJ|Valor do FEEF-RJ|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("IT_VALFEEF","MT100",M->D1_VALFEEF)` |||N|||||
H5|D1_VALFET|N|14|2|Vlr. Fethab|Valor do Fethab|`@E 999,999,999.99` |`MaFisRef("IT_VALFET","MT100",M->D1_VALFET)` |||N|A|R|||
H6|D1_TRIBMUN|C|20|0|C. Trib. Mun|Cód. Trib. Municipal|`@!` |`MaFisRef("IT_TRIBMU","MT100",M->D1_TRIBMUN)` |||S|A|R|||
H7|D1_VALFAB|N|14|2|Vlr. Fabov|Valor do Fabov|`@E 999,999,999.99` |`MaFisRef("IT_VALFAB","MT100",M->D1_VALFAB)` |||N|A|R|||
H8|D1_VALFAC|N|14|2|Vlr. Facs|Valor do Facs|`@E 999,999,999.99` |`MaFisRef("IT_VALFAC","MT100",M->D1_VALFAC)` |||N|A|R|||
H9|D1_VALPMAJ|N|14|2|Val. PIS M.|Valor PIS Majorada|`@E 99,999,999,999.99` |`MaFisRef("IT_VALPMAJ","MT100",M->D1_VALPMAJ)` |||S|A|R|||
I0|D1_VALPS3|N|14|2|Vl. Pis ST|Valor Pis ST|`@E 999,999,999.99` |`Positivo().And.MaFisRef("IT_VALPS3","MT100",M->D1_VALPS3)` |||N|||||
I1|D1_VALINA|N|14|2|Vlr INSS Ad|Valor do INSS Cond. Esp.|`@E 99,999,999,999.99` |`MaFisRef("IT_VALINA","MT100",M->D1_VALINA)` |||N|A|R|||
I2|D1_SLDDEP|N|14|2|Sld.Depend.|Saldo Dependente|`@E 99,999,999,999.99` ||||N|A|R|||
I3|D1_SERVINC|C|3|0|Vinc. Serie|Serie do Doc. de Vinculo|`!!!` |`Vazio() .OR. NfeVldVinc(2)` |||N|A|R|||
I4|D1_TNATREC|C|4|0|Tab.Nat.Rec.|Tab. Nat. Receita|`@!` |`MAFISREF("IT_TABNTRE","MT100",M->D1_TNATREC)` |||N|V|R|||
I5|D1_TPREPAS|C|6|0|Tipo Repasse|Tipo de Repasse|`@!` |`Vazio() .or. ExistCpo("SX5","0G"+M->D1_TPREPAS)` |||N|A|R|||
I6|D1_VALACRS|N|16|2|Vlr.Acresc.|Valor Acrescimo do Item|`@E 999,999,999,999.99` ||||S|V|R|||
I7|D1_VALANTI|N|14|2|Val Ant.ICMS|Valor Antecipação ICMS|`@E 99,999,999,999.99` |`MaFisRef("IT_VALANTI","MT100",M->D1_VALANTI)` ||||||||
I8|D1_VALCF3|N|14|2|Vl. Cof ST|Valor Cofins ST|`@E 999,999,999.99` |`Positivo().And.MaFisRef("IT_VALCF3","MT100",M->D1_VALCF3)` |||S|||||
I9|D1_VALCMAJ|N|14|2|Val. COF M.|Valor COFINS Majorada|`@E 99,999,999,999.99` |`MaFisRef("IT_VALCMAJ","MT100",M->D1_VALCMAJ)` |||S|A|R|||
J0|D1_VALCOF|N|14|2|Valor Cofins|Valor do Cofins|`@E 99,999,999,999.99` |`MaFisRef("IT_VALCOF","MT100",M->D1_VALCOF)` ||||||||
J1|D1_VALCPB|N|14|2|Valor CPRB|Valor da CPRB|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("IT_VALCPB","MT100",M->D1_VALCPB)` |||S|A|R|||
J2|D1_VALCPM|N|14|2|Vl.ISS CPM|Valor ISS CPM|`@E 99,999,999,999.99` |`MaFisRef("IT_VALCPM","MT100",M->D1_VALCPM)` ||||||||
J3|D1_VRETSUB|N|14|2|Ret. Sub.|Retenção Subcontratada|`@E 99,999,999,999.99` ||||S|A|R|||
J4|D1_VLSENAR|N|14|2|Vl.Senar|Valor do Senar|`@E 99,999,999,999.99` |`MaFisRef("IT_VLSENAR","MT100",M->D1_VLSENAR)` ||||||||
J5|D1_VLCIDE|N|14|2|Vl.Cide|Valor do Cide|`@E 99,999,999,999.99` |`MaFisRef("IT_VALCIDE","MT100",M->D1_VLCIDE)` ||||||||
J6|D1_DEDUCAO|N|14|2|Dedução|Dedução|`@E 99,999,999,999.99` ||||N|A|R||`A120RDFRM("WHEN")` |
J7|D1_DTFIMNT|D|8|0|Dt.Fim N.R.|Dt.Fim Nat.Receita||`MAFISREF("IT_DATNTRE","MT100",M->D1_DTFIMNT)` |||N|V|R|||
J8|D1_DFABRIC|D|8|0|Data Fabric.|Data de Fabricação Lote||`M->D1_DFABRIC<=DDATABASE` |||S|A||||
J9|D1_DIFAL|N|14|2|ICMS Difal|ICMS Comple. UF Destino|`@E 99,999,999,999.99` |`MaFisRef("IT_DIFAL","MT100",M->D1_DIFAL)` |||N|A|R|||
K0|D1_CRDZFM|N|14|2|Cred. ZFM|Cred.Zona Franca Manaus|`@E 999,999,999.99` |`MaFisRef("IT_CRDZFM","MT100",M->D1_CRDZFM)` |||N|A|R|||
K1|D1_CRPRSIM|N|14|2|Crd Pres Sim|Crd Pres Sim Nac.- SC|`@E 99,999,999,999.99` |`MaFisRef("IT_CRPRSIM","MT100",M->D1_CRPRSIM)` |||N|A|R|||
K2|D1_CSOSN|C|3|0|Cód Sit SN|Cód Sit Ope SN|`@!` |`MaFisRef("IT_CSOSN","MT100",M->D1_CSOSN)` |||N|A|R|||
K3|D1_CTAREC|C|20|0|Cta Receita|Conta Receita|`@!` |`Vazio() .Or. Ctb105Cta()` ||CT1||V|R|||
K4|D1_ITEMMED|C|1|0|It. Medicao|Item de Medição||||||V|V|||
K5|D1_ITEMNE|C|3|0|Item Nt Emp|Item da Nota de Empenho|`@!` |||||V|R|||
K6|D1_IDSB1|C|20|0|ID Hist. SB1|ID Hist. SB1|`@!` |`MaFisRef("IT_IDSB1","MT100",M->D1_IDSB1)` |||N||R|||
K7|D1_IDSB5|C|20|0|ID Hist. SB5|ID Hist. SB5|`@!` |`MaFisRef("IT_IDSB5","MT100",M->D1_IDSB5)` |||N||R|||
K8|D1_IDSBZ|C|20|0|ID Hist. SBZ|ID Hist. SBZ|`@!` |`MaFisRef("IT_IDSBZ","MT100",M->D1_IDSBZ)` |||N||R|||
K9|D1_ICMSDIF|N|14|2|Vlr.ICMS Dif|Valor do ICMS Diferido|`@E 99,999,999,999.99` |`Positivo().And.MaFisRef("IT_ICMSDIF","MT100",M->D1_ICMSDIF)` |||N|A|R|||
L0|D1_IDCFC|C|20|0|ID Hist CFC|ID Histórico CFC|`@!` |`MaFisRef("IT_IDCFC","MT100",M->D1_IDCFC)` |||N|V|R|||
L1|D1_IDDCF|C|6|0|Id DCF|Identificador DCF|`@!` ||||N|A|R|||
L2|D1_GRUPONC|C|2|0|Grp.Nat.Rec.|Grupo Nat. Receita|`@!` |`MAFISREF("IT_GRPNTRE","MT100",M->D1_GRUPONC)` |||N|V|R|||
L3|D1_HREXPO|C|8|0|Hr. Ult. Exp|Hora da última Exportação|||||N|V|R|||
L4|D1_GRPCST|C|3|0|Enq. IPI|Cod. Enquadramento do IPI|`@!` |`MaFisRef("IT_GRPCST","MT100",M->D1_GRPCST)` ||F08|N|A|R|||
L5|D1_FTRICMS|N|8|5|Fat.Desc.ICM|Fator de Redução Desc.ICM|`@E 99.99999` |`MaFisRef("IT_FTRICMS","MT100",M->D1_FTRICMS)` |||N|A|R|||
L6|D1_ESTCRED|N|16|2|Vlr Est Cred|Valor Estorno Credito|`@E 9,999,999,999.99` |`MaFisRef("IT_ESTCRED","MT100",M->D1_ESTCRED)` |||N|A|R|||
L7|D1_EXPSOP|D|8|0|Export.S&OP|Data da exportação S&OP|||||N|V|R|||
L8|D1_FATDIRE|N|14|2|Fat Direto|Faturamento Direto|`@E 99,999,999,999.99` ||||N|A|R||`A120RDFRM("WHEN")` |
L9|D1_PRUNDA|N|14|2|Vlr. Unit DA|Valor Unitario D.A.|`@E 999,999,999.99` |||||||||
M0|D1_QTDCONF|N|12|4|Qtd confere|Qtd conferida via coletor|||||N|A|R|||
M1|D1_RETENCA|N|14|2|Retenção|Retenção|`@E 99,999,999,999.99` ||||N|A|R||`A120RDFRM("WHEN")` |
M2|D1_REVISAO|C|3|0|Rev.Estrutur|Revisão da Estrutura|`@!` |||||A|R|||
M3|D1_NFVINC|C|9|0|Vinculo Doc.|Vinculo do Doc. de Saida|`@!` |`Vazio() .OR. NfeVldVinc(1)` |||N|A|R|||
M4|D1_MSEXP|C|8|0|Ident.Exp.|Ident.Exp.Dados|||||N|V|R|||
M5|D1_MARGEM|N|6|2|Solid. Entra|% Lucro Calc. Solid.Entra|`@E 999.99` |`Mafisref("IT_MARGEM","MT100",M->D1_MARGEM)` |||N|A|R|||
M6|D1_ITMVINC|C|4|0|Item Vinculo|Item do Doc. de Vinculo|`@!` |`Vazio() .OR. NfeVldVinc(3)` |||N|A|R|||
M7|D1_IDTRIB|C|36|0|ID Tributos|ID dos Tributos|`@!` ||||N|V|R|||
M8|D1_ALIQCPB|N|5|2|Alíq. CPRB|Alíquota CPRB|`@E 99.99` |`Positivo() .And. MaFisRef("IT_ALIQCPB","MT100",M->D1_ALIQCPB)` |||S|A|R|||
M9|D1_ALIQFAB|N|5|2|Aliq. Fabov|Aliquota do Fabov|`@E 99.99` |`MaFisRef("IT_ALIQFAB","MT100",M->D1_ALIQFAB)` |||N|A|R|||
N0|D1_ALIQFAC|N|5|2|Aliq. Facs|Aliquota do Facs|`@E 99.99` |`MaFisRef("IT_ALIQFAC","MT100",M->D1_ALIQFAC)` |||N|A|R|||
N1|D1_ALIQFET|N|5|2|Aliq. Fethab|Aliquota do Fethab|`@E 99.99` |`MaFisRef("IT_ALIQFET","MT100",M->D1_ALIQFET)` |||N|A|R|||
N2|D1_ALIQINA|N|5|2|Aliq INSS Ad|Aliquota do INSS Condiçõe|`@E 99.99` |`MaFisRef("IT_ALIQINA","MT100",M->D1_ALIQINA)` |||N|A|R|||
N3|D1_ALIQCF3|N|5|2|Al. Cof ST|Aliquota Cofins ST|`@E 99.99` |`Positivo().And.MaFisRef("IT_ALIQCF3","MT100",M->D1_ALIQCF3)` |||S|||||
N4|D1_ALFCCMP|N|6|2|FECP Comp.|FECP ICMS complementar|`@E 999.99` |`MaFisRef("IT_ALFCCMP","MT100",M->D1_ALFCCMP)` |||N|A|R|||
N5|D1_ALIQPS3|N|5|2|Al. Pis ST|Aliquota Pis ST|`@E 99.99` |`Positivo().And.MaFisRef("IT_ALIQPS3","MT100",M->D1_ALIQPS3)` |||S|||||
N6|D1_ALIQSOL|N|6|2|Aliq ICMS So|Aliq ICMS Solidario|`@E 999.99` |`MaFisRef("IT_ALIQSOL","MT100",M->D1_ALIQSOL)` ||||||||
N7|D1_ALQCIDE|N|5|2|Aliq.Cide|Aliquota de Cide|`@E 99.99` |`MaFisRef("IT_ALQCIDE","MT100",M->D1_ALQCIDE)` ||||||||
N8|D1_ALQCPM|N|5|2|Alq.ISS CPM|Aliquota ISS CPM|`@E 99.99` |`MaFisRef("IT_ALQCPM","MT100",M->D1_ALQCPM)` ||||||||
N9|D1_ABATALM|N|14|2|Abat. Alim.|Abatimento Alimentação|`@E 99,999,999,999.99` ||||S|A|R|||
O0|D1_ABATINS|N|14|2|Abatim. INSS|Valor abatimento / INSS|`@E 99,999,999,999.99` |`MaFisRef("IT_ABVLINSS","MT100",M->D1_ABATINS)` |||N|A|R|||
O1|D1_ABATISS|N|14|2|Abatim. ISS|Valor abatimento / ISS|`@E 99,999,999,999.99` |`MaFisRef("IT_ABVLISS","MT100",M->D1_ABATISS)` |||S|A|R|||
O2|D1_ABATMAT|N|14|2|Abat. Mat.|Abatimento ISS material|`@E 99,999,999,999.99` |`MaFisRef("IT_ABMATISS","MT100",M->D1_ABATMAT)` |||N|A|R|||
O3|D1_ABATTRA|N|14|2|Abat. Tran.|Abatimento Transportes|`@E 99,999,999,999.99` ||||S|A|R|||
O4|D1_CODISS|C|9|0|Cod.Serv.ISS|Código de Serviço do ISS|`@9` |`MaFisRef("IT_CODISS","MT100",M->D1_CODISS)` |||N|A|R|||
O5|D1_CODDIS|C|6|0|Cod Distrib|Código Distribuição|`@!` ||||N|A|R|||
O6|D1_CONIMP|N|9|4|Cont. Imp.|Conteudo de Importacao|`@E 9,999.9999` ||||N|A|R|||
O7|D1_CONBAR|C|1|0|Conferencia|Conferencia Cod.Barras|`@!` ||"0"||N|A|R|||
O8|D1_CODNE|C|12|0|Cod Nota Emp|Cód. da Nota de Empenho|`@!` |`ExistCpo( "CX1", M->D1_CODNE)` ||CX1||V|R|||
O9|D1_CODNOR|C|6|0|Cod. Norma|Codigo da Norma|`999999` |`ExistCpo("DC2")` ||DC2|N|A|R|||
P0|D1_CNATREC|C|3|0|Cod.Nat.Rec.|Código Nat. Receita|`@!` |`MAFISREF("IT_CODNTRE","MT100",M->D1_CNATREC)` |||N|V|R|||
P1|D1_CFPS|C|6|0|Cod. CFPS|Código CFPS|`@9` |`MaFisRef("IT_CFPS","MT100",M->D1_CFPS)` ||||||||
P2|D1_BASFEEF|N|14|2|Bas.FEEF.RJ|Base FEEF-RJ|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("IT_BASFEEF","MT100",M->D1_BASFEEF)` |||N|||||
P3|D1_BSSENAR|N|14|2|Base Senar|Base do Senar|`@E 99,999,999,999.99` |`MaFisRef("IT_BSSENAR","MT100",M->D1_BSSENAR)` ||||||||
P4|D1_BASEFAB|N|14|2|Base Fabov|Base do Fabov|`@E 999,999,999.99` |`MaFisRef("IT_BASEFAB","MT100",M->D1_BASEFAB)` |||N|A|R|||
P5|D1_BASEFAC|N|14|2|Base Facs|Base do Facs|`@E 999,999,999.99` |`MaFisRef("IT_BASEFAC","MT100",M->D1_BASEFAC)` |||N|A|R|||
P6|D1_BASEFET|N|14|2|Base Fethab|Base do Fethab|`@E 999,999,999.99` |`MaFisRef("IT_BASEFET","MT100",M->D1_BASEFET)` |||N|A|R|||
P7|D1_ALQFEEF|N|5|2|Aliq.FEEF.RJ|Alíquota FEEF-RJ|`@E 99.99` |`Positivo() .And. MaFisRef("IT_ALQFEEF","MT100",M->D1_ALQFEEF)` |||N|||||
P8|D1_BASEFMP|N|14|2|Base FUMIPEQ|Base de Cálculo FUMIPEQ|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEFMP","MT100",M-> D1_BASEFMP)` ||||||||
P9|D1_AVLINSS|N|14|2|Ab. Val INSS|Abat INSS Subcontratada|`@E 99,999,999,999.99` |`MaFisRef("IT_AVLINSS","MT100",M->D1_AVLINSS)` |||N|A|R|||
Q0|D1_BASECF3|N|14|2|Bs. Cof ST|Base Cofins ST|`@E 999,999,999.99` |`Positivo().And.MaFisRef("IT_BASECF3","MT100",M->D1_BASECF3)` |||S|||||
Q1|D1_BASECID|N|14|2|Base Cide|Base de Calculo Cide|`@E 99,999,999,999.99` |`MaFisRef("IT_BASECID","MT100",M->D1_BASECID)` ||||||||
Q2|D1_BASECOF|N|14|2|Base Cofins|Base do Cofins|`@E 99,999,999,999.99` |`MaFisRef("IT_BASECOF","MT100",M->D1_BASECOF)` ||||||||
Q3|D1_BASECPB|N|14|2|Base CPRB|Base CPRB|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("IT_BASECPB","MT100",M->D1_BASECPB)` |||S|A|R|||
Q4|D1_BASECPM|N|14|2|Bs.ISS CPM|Base ISS CPM|`@E 99,999,999,999.99` |`MaFisRef("IT_BASECPM","MT100",M->D1_BASECPM)` ||||||||
Q5|D1_BASECSL|N|14|2|Base CSLL|Base do CSLL|`@E 99,999,999,999.99` |`MaFisRef("IT_BASECSL","MT100",M->D1_BASECSL)` ||||||||
Q6|D1_BASEPS3|N|14|2|Bs. Pis ST|Base Pis ST|`@E 999,999,999.99` |`Positivo().And.MaFisRef("IT_BASEPS3","MT100",M->D1_BASEPS3)` |||S|||||
Q7|D1_ALSENAR|N|5|2|Aliq.Senar|Aliquota Senar|`@E 99.99` |`MaFisRef("IT_ALSENAR","MT100",M->D1_ALSENAR)` ||||||||
Q8|D1_BASEINA|N|14|2|Base INSS Ad|Base do INSS Condições Es|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEINA","MT100",M->D1_BASEINA)` |||N|A|R|||
Q9|D1_BASEINP|N|14|2|Bas.INSS.Pt|Base do INSS Patronal|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("IT_BASEINP","MT100",M->D1_BASEINP)` |||S|A|R|||
R0|D1_BASEPIS|N|14|2|Base Pis|Base do Pis|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEPIS","MT100",M->D1_BASEPIS)` ||||||||
R1|D1_BASEPRO|N|14|2|Bas.PROT.GO|Base PROTEGE-GO|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("IT_BASEPRO","MT100",M->D1_BASEPRO)` ||||||||
R2|D1_BASESES|N|14|2|Base do SEST|Base do SEST/SENAT|`@E 999,999,999.99` |`MaFisRef("IT_BASESES","MT100",M->D1_BASESES)` |||N|||||
R3|D1_BASFECP|N|14|2|Base FCP Pr.|Base FCP Próprio|`@E 99,999,999,999.99` |`MaFisRef("IT_BASFECP","MT100",M->D1_BASFECP)` |||S|A|R|||
R4|D1_BASEFUN|N|14|2|Bas.FUNRURAL|Base de Calculo FUNRURAL|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEFUN","MT100",M->D1_BASEFUN)` |||N|V||||
R5|D1_ALQFMD|N|5|2|Aliq. Famad|Aliquota do Famad|`@E 99.99` |`MaFisRef("IT_ALQFMD","MT100",M->D1_ALQFMD)` |||S|A|R|||
R6|D1_ALQFMP|N|5|2|Aliq. FUMIPE|Aliquota de FUMIPEQ|`@E 99.99` |`MaFisRef("IT_ALQFMP","MT100",M-> D1_ALQFMP)` ||||||||
R7|D1_BASEFMD|N|14|2|Base Famad|Base do Famad|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEFMD","MT100",M->D1_BASEFMD)` |||N|A|R|||
R8|D1_BSFCCMP|N|14|2|Base FCP Cmp|Base FCP Complementar|`@E 99,999,999,999.99` |`MaFisRef("IT_BSFCCMP","MT100",M->D1_BSFCCMP)` |||S|A|R|||
R9|D1_BSFCPST|N|14|2|Base FCP ST|Base FCP ST|`@E 99,999,999,999.99` |`MaFisRef("IT_BSFCPST","MT100",M->D1_BSFCPST)` |||S|A|R|||
S0|D1_BASNDES|N|14|2|B.ICMS ST An|Base ICMS ST Anterior|`@E 99,999,999,999.99` |`MaFisRef("IT_BASNDES","MT100",M->D1_BASNDES) .And. Positivo()` |||N|A|R|||
S1|D1_BFCPANT|N|14|2|Base FCP Ant|Base FCP Rec. Ant.|`@E 99,999,999,999.99` |`MaFisRef("IT_BFCPANT","MT100",M->D1_BFCPANT)` |||S|A|R|||
S2|D1_CODROM|C|10|0|Romaneio|Romaneio Originação|`@!` ||||N|A|R|||
S3|D1_CODSAF|C|15|0|Cód. Safra|Código da Safra|`@!` |`Vazio().Or.ExistCpo('NJU')` |||N|A|R|||
S4|D1_CODBAIX|C|6|0|C. Bem Princ|Cod. Bem Principal|`@!` |`Vazio() .Or. ExistCPO("SF9")` ||SF9|S|A|R|||
S5|D1_CODLAN|C|6|0|Cod.Cat83|Código Lançamento Cat83|`@!` |`Vazio() .Or. ExistCpo('CDZ')` ||CDZ|S|A|R|||
S6|D1_AFCPANT|N|6|2|Aliq FCP Ant|Alíquota do FCP Rec. Ant.|`@E 999.99` |`MaFisRef("IT_AFCPANT","MT100",M->D1_AFCPANT)` |||S|A|R|||
S7|D1_ALQCSL|N|6|2|Aliq. CSLL|Aliquota CSLL|`@E 999.99` |`MaFisRef("IT_ALIQCSL","MT100",M->D1_ALQCSL)` ||||||||
S8|D1_ALQFECP|N|6|2|Aliq. FECP|Alíquota do FECP|`@E 999.99` |`MaFisRef("IT_ALIQFECP","MT100",M->D1_ALQFECP)` |||S|A|R|||
S9|D1_ALQCOF|N|6|2|Aliq. Cofins|Aliquota do Cofins|`@E 999.99` |`MaFisRef("IT_ALIQCOF","MT100",M->D1_ALQCOF)` ||||||||
T0|D1_ALMTERC|C|2|0|Armz Terc.|Armazem de Terceiros|`@!` |`IsAlmTerc(M->D1_ALMTERC)` ||||||||
T1|D1_ALIQSES|N|5|2|Aliq. SEST|Aliquota do SEST/SENAT|`@E 99.99` |`MaFisRef("IT_ALIQSES","MT100",M->D1_ALIQSES)` |||N|||||
T2|D1_ALQNDES|N|6|2|A.ICMS ST An|Aliq. ICMS ST Anterior|`@E 999.99` |`MaFisRef("IT_ALQNDES","MT100",M->D1_ALQNDES)` |||S|A|R|||
T3|D1_ALQPIS|N|6|2|Aliq. Pis|Aliquota do PIS|`@E 999.99` |`MaFisRef("IT_ALIQPIS","MT100",M->D1_ALQPIS)` ||||||||
T4|D1_ALFCPST|N|6|2|Aliq. FCP ST|Alíquota do FCP ST|`@E 999.99` |`MaFisRef("IT_ALFCST","MT100",M->D1_ALFCPST)` |||S|A|R|||
T5|D1_ALIQPRO|N|5|2|Aliq.PROT.GO|Aliquota PROTEGE-GO|`@E 99.99` |`Positivo().And. MaFisRef("IT_ALIQPRO","MT100",M->D1_ALIQPRO)` ||||||||
T6|D1_ALIQFUN|N|6|2|Alq FUNRURAL|Aliquota FUNRURAL|`@E 999.99` |`MaFisRef("IT_PERFUN","MT100",M->D1_ALIQFUN)` |||N|V|R|||
T7|D1_ALIQII|N|6|2|Aliq Import|Aliq Imp Importação|`@E 999.99` |`Positivo() .And. MaFisRef("IT_ALIQII","MT100",M->D1_ALIQII)` |||N|||||
T8|D1_ITEROM|C|2|0|Item Rom.|Item do Romaneio|`@!` ||||N|A|R|||
T9|D1_NFPNUM|C|9|0|NFP Num.|NF Propria Número|`@!` ||||N|A|R|||
U0|D1_NFPSER|C|3|0|NFP Serie|NF Própia Série|`@!` ||||N|A|R|||
U1|D1_NUMPED|C|15|0|Nº Pedido|Nº de Pedido|`@!` ||||N|V|R|||
U2|D1_OKISS|C|2|0|Marca|Marca|`@!` ||||S|A|R|||
U3|D1_RGESPST|C|1|0|Reg.Esp.ST|Regime Especial ST|`@!` |`MaFisRef("IT_RGESPST","MT100",M->D1_RGESPST)` |||S|A|R|1=Sim;2=Não||
U4|D1_SDOC|C|3|0|Série Doc.|Série do Documento Fiscal|`!!!` ||||N|V|R|||
U5|D1_SDOCORI|C|3|0|Série Orig.|Série da N.F. Original|`!!!` ||||N|V|R|||
U6|D1_SDOCREM|C|3|0|Série Doc.|Série do Doc Envio|`!!!` ||||N|V|R|||
U7|D1_SDOCVNC|C|3|0|Vinc. Série|Série do Doc. de Vinculo|`!!!` ||||N|V|R|||
U8|D1_PRFDSUL|N|12|8|Pr.Fundersul|Percentual Fundersul|`@E 999.99999999` |`MaFisRef("IT_PRFDSUL","MT100",M->D1_PRFDSUL)` |||N|A|R|||
U9|D1_PRINCMG|N|6|2|Pr.Inc.Leite|Perc.Incentivo Prod.Leite|`@E 999.99` |`MAFISREF("IT_PRINCMG","MT100",M->D1_PRINCMG)` |||N|V||||
V0|D1_OPERADO|C|3|0|Operador|Operador de Caixa|`@!` ||||N|V|R|||
V1|D1_FCICOD|C|36|0|Codigo FCI|Codigo FCI|`@!` ||||N|A|R|||
V2|D1_FCPAUX|N|7|4|Ind.Fcp.Aux.|Indice Auxiliar do FCP|`@E 99.9999` |`MaFisRef("IT_FCPAUX","MT100",M->D1_FCPAUX)` |||S|A|R|||
V3|D1_GARANTI|C|1|0|Tem Garantia|Insumo Tem Garantia|`@!` |`PERTENCE ("SN") .AND. NGGARANSD1(cAliasTPZ)` |"N"||N|A|R|S=Sim;N=Não||
V4|D1_FILORI|C|2|0|Fil. Doc.Ori|Filial do Docto.de Origem|||||||R|||
V5|D1_ICMNDES|N|14|2|ICMS ST Ante|Valor ICMS ST Anterior|`@E 99,999,999,999.99` |`MaFisRef("IT_ICMNDES","MT100",M->D1_ICMNDES) .And. Positivo()` |||N|A|R|||
V6|D1_IDSF4|C|20|0|ID Hist. SF4|ID Hist. SF4|`@!` |`MaFisRef("IT_IDSF4","MT100",M->D1_IDSF4)` |||N||R|||
V7|D1_IDSF7|C|20|0|ID Hist. SF7|ID Hist. SF7|`@!` |`MaFisRef("IT_IDSF7","MT100",M->D1_IDSF7)` |||N||R|||
V8|D1_CTROG|C|6|0|Ctr. Orig.|Contrato Originação|`@!` |`If(Empty(M->D1_CTROG),.T.,ExistCpo('NJR'))` |||N|A|R|||
V9|D1_CRPREPR|N|14|2|Cre.Pres. PR|Credito Presumido Parana|`@E 99,999,999,999.99` |`MaFisRef("IT_CRPREPR","MT100",M->D1_CRPREPR)` |||N|A|R|||
W0|D1_CRPRESC|N|14|2|Crd Pres SC|Crd Presumido - SC|`@E 9,999,999,999.99` |`MaFisRef("IT_CRPRESC","MT100",M->D1_CRPRESC)` |||N|A|R|||
W1|D1_CUSRP1|N|14|2|C Reposicao|Custo de Reposicao|`@E 999,999,999.99` ||||N|||||
W2|D1_CUSRP2|N|14|2|Repos.2a M|Custo de Reposicao 2a M|`@E 999,999,999.99` ||||N|||||
W3|D1_CUSRP3|N|14|2|C Repos.3a M|Custo de Reposicao 3a M|`@E 999,999,999.99` ||||N|||||
W4|D1_CUSRP4|N|14|2|C Repos.4a M|Custo de Reposicao 4a M|`@E 999,999,999.99` ||||N|||||
W5|D1_CUSRP5|N|14|2|C Repos.5a M|Custo de Reposicao 5a M|`@E 999,999,999.99` ||||N|||||
W6|D1_DESCZFC|N|14|2|Val.Cof.ZFM|Val. desc. do Cof para ZF|`@E 99,999,999,999.99` |`MaFisRef("IT_DESCZFCOF","MT100",M->D1_DESCZFC)` |||N|V|R|||
W7|D1_DESCZFP|N|14|2|Val.Pis.ZFM|Val. desc. do PIS para ZF|`@E 99,999,999,999.99` |`MaFisRef("IT_DESCZFPIS","MT100",M->D1_DESCZFP)` |||N|V|R|||
W8|D1_DESCZFR|N|14|2|Desc.Z.Franc|Desconto venda Z.Franca|`@E 99,999,999,999.99` |`MaFisRef("IT_DESCZF","MT100",M->D1_DESCZFR)` |||N|V|R|||
W9|D1_VLINCMG|N|14|2|Vl.Inc.Leite|Vl.Incentivo Prod.Leite|`@E 99,999,999,999.99` |`MAFISREF("IT_VLINCMG","MT100",M->D1_VLINCMG)` |||N|V||||
X0|D1_VOPDIF|N|16|2|Vlr.OP.Dif|Valor da Operação|`@E 9,999,999,999,999.99` |`Positivo().And.MaFisRef("IT_VOPDIF","MT100",M->D1_VOPDIF)` |||S|A|R|||
X1|D1_VALCSL|N|14|2|Valor CSLL|Valor do CSLL|`@E 99,999,999,999.99` |`MaFisRef("IT_VALCSL","MT100",M->D1_VALCSL)` |||S|A|R|||
X2|D1_TRANSIT|C|1|0|Status Trans|Status para Amz. transito|`@!` ||||N|||||
X3|D1_SLDEXP|N|11|2|Sld. Export.|Saldo Exportação Indireta|`@E 99,999,999.99` |`Positivo()` |||N|V|R|||
X4|D1_VALPIS|N|14|2|Valor PIS|Valor do PIS|`@E 99,999,999,999.99` |`MaFisRef("IT_VALPIS","MT100",M->D1_VALPIS)` ||||||||
X5|D1_VALSES|N|14|2|Valor SEST|Valor do SEST/SENAT|`@E 999,999,999.99` |`MaFisRef("IT_VALSES","MT100",M->D1_VALSES)` |||N|||||
X6|D1_VFCPANT|N|14|2|Vlr. FCP Ant|Valor do FCP Rec. Ant.|`@E 99,999,999,999.99` |`MaFisRef("IT_VFCPANT","MT100",M->D1_VFCPANT)` |||S|A|R|||
X7|D1_VFECPST|N|14|2|Vlr FCP ST|Valor do FCP ST|`@E 99,999,999,999.99` |`MaFisRef("IT_VFECPST","MT100",M->D1_VFECPST)` |||S|A|R|||
X8|D1_VALPRO|N|14|2|Val.PROT.GO|Valor do PROTEGE-GO|`@E 99,999,999,999.99` |`Positivo().And. MaFisRef("IT_VALPRO","MT100",M->D1_VALPRO)` ||||||||
X9|D1_VALFDS|N|14|2|Vl.Fundersul|Valor do Fundersul|`@E 99,999,999,999.99` |`MaFisRef("IT_VALFDS","MT100",M->D1_VALFDS)` |||N|A|R|||
Y0|D1_VALFECP|N|14|2|Vlr FCP Prop|Valor do FCP Próprio|`@E 99,999,999,999.99` |`MaFisRef("IT_VALFECP","MT100",M->D1_VALFECP)` |||S|A|R|||
Y1|D1_UFERMS|N|14|2|UFERMS|Valor UFERMS|`@E 99,999,999,999.99` |`MaFisRef("IT_UFERMS","MT100",M->D1_UFERMS)` |||N|A|R|||
Y2|D1_VALFMD|N|14|2|Vlr. Famad|Valor do Famad|`@E 99,999,999,999.99` |`MaFisRef("IT_VALFMD","MT100",M->D1_VALFMD)` |||N|A|R|||
Y3|D1_VALFUN|N|14|2|Vlr FUNRURAL|Valor do FUNRURAL|`@E 99,999,999,999.99` |`MaFisRef("IT_FUNRURAL","MT100",M->D2_VALFUN)` |||N|V|R|||


## SIX - Índices da tabela

ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|D1_FILIAL+D1_DOC+D1_SERIE+D1_FORNECE+D1_LOJA+D1_COD+D1_ITEM|Documento + Serie + Forn/Cliente + Loja + Produto + Item NF|XXX+XXX+XXX+XXX+SB1||S|
2|D1_FILIAL+D1_COD+D1_DOC+D1_SERIE+D1_FORNECE+D1_LOJA|Produto + Documento + Serie + Forn/Cliente + Loja|SB1||S|
3|D1_FILIAL+DTOS(D1_EMISSAO)+D1_DOC+D1_SERIE+D1_FORNECE+D1_LOJA|DT Emissao + Documento + Serie + Forn/Cliente + Loja|||S|
4|D1_FILIAL+D1_NUMSEQ|Num.Sequenc.|||S|
5|D1_FILIAL+D1_COD+D1_LOCAL+D1_NUMSEQ|Produto + Armazem + Num.Sequenc.|SB1||S|
6|D1_FILIAL+DTOS(D1_DTDIGIT)+D1_NUMSEQ|DT Digitacao + Num.Sequenc.|||S|
7|D1_FILIAL+D1_COD+D1_LOCAL+DTOS(D1_DTDIGIT)+D1_NUMSEQ|Produto + Armazem + DT Digitacao + Num.Sequenc.|SB1||S|
8|D1_FILIAL+D1_CONHEC+D1_TIPO_NF|Num. Conhec. + Tipo Docto.|||S|
9|D1_FILIAL+D1_ORDEM+D1_COD|Ordem Servic + Produto|||S|
A|D1_FILIAL+D1_FORNECE+D1_LOJA+D1_SERIREM+D1_REMITO+D1_ITEMREM|Forn/Cliente + Loja + Serie remito + Remito + Item remito|FOR||S|
B|D1_FILIAL+D1_DOC+D1_SERIE+D1_FORNECE+D1_LOJA+D1_COD+D1_LOTECTL+D1_NUMLOTE+DTOS(D1_DTVALID)|Documento + Serie + Forn/Cliente + Loja + Produto + Lote + Sub-Lote +||ACDSD101|S|
C|D1_FILIAL+D1_COD+D1_CHASSI|Produto + Chassi|||S|
D|D1_FILIAL+D1_DOC+D1_SDOC+D1_FORNECE+D1_LOJA+D1_COD+D1_ITEM|Documento + Série Doc. + Forn/Cliente + Loja + Produto + Item NF|||N|
E|D1_FILIAL+D1_COD+D1_DOC+D1_SDOC+D1_FORNECE+D1_LOJA|Produto + Documento + Série Doc. + Forn/Cliente + Loja|||N|
F|D1_FILIAL+DTOS(D1_EMISSAO)+D1_DOC+D1_SDOC+D1_FORNECE+D1_LOJA|DT Emissao + Documento + Série Doc. + Forn/Cliente + Loja|||N|
G|D1_FILIAL+D1_FORNECE+D1_LOJA+D1_SDOCREM+D1_REMITO+D1_ITEMREM|Forn/Cliente + Loja + Série Doc. + Remito + Item remito|||N|
H|D1_FILIAL+D1_DOC+D1_SDOC+D1_FORNECE+D1_LOJA+D1_COD+D1_LOTECTL+D1_NUMLOTE+DTOS(D1_DTVALID)|Documento + Série Doc. + Forn/Cliente + Loja + Produto + Lote + Sub-Lo|||N|
I|D1_FILIAL+D1_NUMPED|Nº Pedido|||S|
J|D1_FILIAL+D1_NFORI+D1_SERIORI+D1_FORNECE+D1_LOJA|Docto. Orig. + Serie Orig. + Forn/Cliente + Loja|||S|
K|D1_FILIAL+D1_SERIORI+D1_NFORI|Serie Orig. + Docto. Orig.|||S|
L|D1_FILIAL+D1_SERIREM+D1_REMITO|Serie remito + Remito|||S|
M|D1_FILIAL+D1_PEDIDO+D1_ITEMPC|No do Pedido + Item do Ped.|||N|
N|D1_FILIAL+D1_IDTRIB|ID Tributos|||S|
O|D1_FILIAL+D1_CTAREC|Cta Receita|||S|
P|D1_FILIAL+D1_CONTA|C Contabil|||S|


