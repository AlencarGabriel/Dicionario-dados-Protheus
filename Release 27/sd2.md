# SD2 - Itens de Venda da NF
## SX3 - Campos da tabela

X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|D2_FILIAL|C|2|0|Filial|Filial do Sistema|||||N|||||
02|D2_ITEM|C|2|0|Item|Item da Nota Fiscal|`@!` ||||N|||||
03|D2_COD|C|15|0|Produto|Codigo do Produto|`@!` |`vazio().or.(existcpo("SB1").and. MaFisRef("IT_PRODUTO","MT100",M->D2_COD).And.A920IniCpo())` ||SB1|S|||||
04|D2_SEGUM|C|2|0|Segunda UM|Segunda Unidade de Medida||`ExistCpo("SAH")` ||SAH|N|V||||
05|D2_UM|C|2|0|Unidade|Unidade de Medida||`ExistCpo("SAH")` ||SAH|S|V||||
06|D2_QUANT|N|11|2|Quantidade|Quantidade do Produto|`@E 99999999.99` |`Positivo().and. A100SegUm().And.MaFisRef("IT_QUANT","MT100",M->D2_QUANT)` |||S|||||
07|D2_PRCVEN|N|14|2|Vlr.Unitario|Valor Unitario|`@E 99,999,999,999.99` |`Positivo().And.NaoVazio().And.MaFisRef("IT_PRCUNI","MT100",M->D2_PRCVEN)` |||S|||||
08|D2_TOTAL|N|14|2|Vlr.Total|Valor Total|`@E 99,999,999,999.99` |`Positivo().And.A920Total(M->D2_TOTAL) .and. MaFisRef("IT_VALMERC","MT100",M->D2_TOTAL)` |||N|||||
09|D2_VALIPI|N|14|2|Vlr.IPI|Valor do IPI do Item|`@E 99,999,999,999.99` |`Positivo().And.MaFisRef("IT_VALIPI","MT100",M->D2_VALIPI)` |||N|||||
10|D2_VALICM|N|14|2|Vlr.ICMS|Valor do ICM do Item|`@E 99,999,999,999.99` |`Positivo().And.MaFisRef("IT_VALICM","MT100",M->D2_VALICM)` |||N|||||
11|D2_TES|C|3|0|Tipo Saida|Tipo de Saida da nota|`@9` |`existcpo("SF4").And.MaAvalTes("S",M->D2_TES).And.MaFisRef("IT_TES","MT100",M->D2_TES)` ||SF4|N|||||
12|D2_CF|C|5|0|Cod. Fiscal|Codigo Fiscal da Operacao|`@9` |`NaoVazio().and.AvalCFO("SD2",M->D2_CF) .and. MaFisRef("IT_CF","MT100",M->D2_CF)` ||13|N|||||
13|D2_DESC|N|5|2|Desc.Item|Desconto no Item|`@E 99.99` |`Positivo()` |||N|||||
14|D2_IPI|N|5|2|Aliq. IPI|Alíquota de IPI|`@E 99.99` |`Positivo().And.MaFisRef("IT_ALIQIPI","MT100",M->D2_IPI)` |||N|||||
15|D2_PICM|N|5|2|Aliq. ICMS|Alíquota de ICMS|`@E 99.99` |`Positivo().And.MaFisRef("IT_ALIQICM","MT100",M->D2_PICM)` |||N|||||
16|D2_VALCSL|N|14|2|Valor CSLL|Valor do CSLL|`@E 99,999,999,999.99` |`MaFisRef("IT_VALCSL","MT100",M->D2_VALCSL)` ||||||||
17|D2_PESO|N|10|3|Peso total|Peso do produto rateio|`@E 999999.999` |`Positivo()` |||N|||||
18|D2_CONTA|C|20|0|C Contabil|Codigo da Conta Contabil|`@!` |`Vazio() .Or. Ctb105Cta()` ||CT1|N|||||
19|D2_OP|C|14|0|Ord Producao|Ordem de Producao|`@9` |`vazio().or.existcpo("SC2")` ||SC2|N|||||
20|D2_PEDIDO|C|6|0|No do Pedido|pedido de compra/venda|`@!` |||SC7|N|||||
21|D2_ITEMPV|C|2|0|Item do Ped.|Item do pedido de venda|`@!` ||||N|||||
22|D2_CLIENTE|C|6|0|Cliente|Codigo do Cliente|`@!` ||||S|||||
23|D2_LOJA|C|2|0|Loja|Loja do Cliente|`@!` ||||S|||||
24|D2_LOCAL|C|2|0|Armazem|Codigo do Armazem|`@!` |`ExistCpo("NNR")` ||NNR|N|||||
25|D2_DOC|C|9|0|Num. Docto.|Numero do Documento/Nota|`@!` ||||N|||||
26|D2_SERIE|C|3|0|Serie|Serie da Nota Fiscal|`!!!` ||||S|||||
27|D2_GRUPO|C|4|0|Grupo|Grupo do Produto|`@!` |`ExistCpo("SBM")` ||SBM|N|||||
28|D2_TP|C|2|0|Tipo Produto|Tipo do Produto Vendido|`@!` ||||N|||||
29|D2_EMISSAO|D|8|0|Emissao|Data de Emissao|||ddatabase||S|||||
30|D2_CUSTO1|N|14|2|Custo|Custo|`@E 999,999,999.99` ||||N|||||
31|D2_CUSTO2|N|14|2|Custo Moeda2|Custo da Moeda 2|`@E 999,999,999.99` ||||N|||||
32|D2_CUSTO3|N|14|2|Custo Moeda3|Custo da Moeda 3|`@E 999,999,999.99` ||||N|||||
33|D2_CUSTO4|N|14|2|Custo Moeda4|Custo da Moeda 4|`@E 999,999,999.99` ||||N|||||
34|D2_CUSTO5|N|14|2|Custo Moeda5|Custo da Moeda 5|`@E 999,999,999.99` ||||N|||||
35|D2_PRUNIT|N|14|2|Prc Tabela|Preco de Tabela|`@E 99,999,999,999.99` |`Positivo()` |||N|||||
36|D2_QTSEGUM|N|11|2|Qtde 2a UM|Segunda Unidade de Medida|`@E 99,999,999.99` |`Positivo()` |||N|||||
37|D2_NUMSEQ|C|6|0|Num.Sequenc.|Numeracao sequencial|`@!` ||||N|||||
38|D2_EST|C|2|0|Estado Dest.|Estado de Destino da Merc|`@!` |`ExistCpo("SX5","12"+M->D2_EST)` |||N|||||
39|D2_DESCON|N|12|2|Desconto|Desconto do Item de Venda|`@E 999,999,999.99` |`Positivo() .AND. MaFisRef("IT_DESCONTO","MT100",M->D2_DESCON)` |||N|||||
40|D2_TIPO|C|1|0|Tipo de N.F.|Tipo de Nota Fiscal|||||N|||||
41|D2_NFORI|C|9|0|N.F.Original|N.Fiscal Original|`@!` |`MaFisRef("IT_NFORI","MT100",M->D2_NFORI)` |||N|||||
42|D2_SERIORI|C|3|0|Serie Orig.|Serie da N.F. Original|`!!!` |`MaFisRef("IT_SERORI","MT100",M->D2_SERIORI)` |||N|||||
43|D2_QTDEDEV|N|11|2|Qtde Devol.|Qtde Devolvida|`@E 99,999,999.99` ||||N|||||
44|D2_VALDEV|N|14|2|Valor Devol.|Valor Devolvido|`@E 9,999,999,999.99` ||||N|||||
45|D2_ORIGLAN|C|2|0|Orig. Lancto|Origem do Lancamento|`@!` ||||N|||||
46|D2_BRICMS|N|14|2|Ret. ICMS|Base de Retencao ICMS|`@E 99,999,999,999.99` |`Positivo().And.MaFisRef("IT_BASESOL","MT100",M->D2_BRICMS)` |||N|||||
47|D2_BASEORI|N|16|2|B.Orig ICMS|Base Original do ICMS|`@E 999,999,999,999.99` ||||N|||||
48|D2_BASEICM|N|16|2|Base ICMS|Base do ICMS do Item|`@E 9,999,999,999,999.99` |`Positivo().And.MaFisRef("IT_BASEICM","MT100",M->D2_BASEICM)` |||N|||||
49|D2_VALACRS|N|16|2|Vlr.Acresc.|Valor Acrescimo do Item|`@E 999,999,999,999.99` ||||N|||||
50|D2_IDENTB6|C|6|0|Ident. PD3|Identificador no Poder 3|||||N|V||||
51|D2_CODISS|C|9|0|Cod.Serv.ISS|Código de Serviço do ISS|`@9` |`MaFisRef("IT_CODISS","MT100",M->D2_CODISS)` ||60|N|||||
52|D2_GRADE|C|1|0|Grade|Item referente a Grade|`@!` ||||N|||||
53|D2_SEQCALC|C|14|0|Seq.Recalc.|Seq.Recalc.Custo Médio|||||N|||||
54|D2_ICMSRET|N|14|2|ICMS Solid.|Valor do ICMS Solidario|`@E 99,999,999,999.99` |`Positivo().And.MaFisRef("IT_VALSOL","MT100",M->D2_ICMSRET)` |||N|||||
55|D2_COMIS1|N|5|2|Comissao 1|Percentual Comissao 1|`@E 99.99` |`positivo() .Or. Vazio()` |||N|||||
56|D2_COMIS2|N|5|2|Comissao 2|Percentual Comissao 2|`@E 99.99` |`positivo() .Or. Vazio()` |||N|||||
57|D2_COMIS3|N|5|2|Comissao 3|Percentual Comissao 3|`@E 99.99` |`positivo() .Or. Vazio()` |||N|||||
58|D2_COMIS4|N|5|2|Comissao 4|Percentual Comissao 4|`@E 99.99` |`positivo() .Or. Vazio()` |||N|||||
59|D2_COMIS5|N|5|2|Comissao 5|Percentual Comissao 5|`@E 99.99` |`positivo() .Or. Vazio()` |||N|||||
60|D2_LOTECTL|C|10|0|Lote|Lote||`LocXVlot()` |||N|||||
61|D2_NUMLOTE|C|6|0|Sub-Lote|Sub-Lote||`LocXVlot()` |||N|||||
62|D2_DTVALID|D|8|0|Valid. Lote|Validade do Lote Inform.||`M->D2_DTVALID >= dDataBase` |||N|V||||
63|D2_DESCZFR|N|14|2|Desc.Z.Franc|Desconto venda Z.Franca|`@E 99,999,999,999.99` |`MaFisRef("IT_DESCZF","MT100",M->D2_DESCZFR)` |||N|||||
64|D2_PDV|C|10|0|Número PDV|N·mero do PDV do SIGALOJA|`@!` ||||N|||||
65|D2_NUMSERI|C|20|0|Num de Serie|Num de Serie do Produto|`@!` ||||N|||||
66|D2_DTLCTCT|D|8|0|Dt. do Lanc.|Data do Lanc. Contab.|||||N|||||
67|D2_CUSFF1|N|14|2|Custo FIFO 1|Custo FIFO Moeda 1|`@E 999,999,999.99` ||||N|||||
68|D2_CUSFF2|N|14|2|Custo FIFO 2|Custo FIFO Moeda 2|`@E 999,999,999.99` ||||N|||||
69|D2_CUSFF3|N|14|2|Custo FIFO 3|Custo FIFO Moeda 3|`@E 999,999,999.99` ||||N|||||
70|D2_CUSFF4|N|14|2|Custo FIFO 4|Custo FIFO Moeda 4|`@E 999,999,999.99` ||||N|||||
71|D2_CUSFF5|N|14|2|Custo FIFO 5|Custo FIFO Moeda 5|`@E 999,999,999.99` ||||N|||||
72|D2_CLASFIS|C|3|0|Sit.Tribut.|Situacao Tributaria|`@!` |`MAFISREF("IT_CLASFIS","MT100",M->D2_CLASFIS)` |||N|||||
73|D2_REMITO|C|9|0|Remito|Remito|`@!` |||||V||||
74|D2_BASIMP1|N|14|2|Base Imp. 1|Base de Calculo Imposto 1|`@E  99,999,999,999.99` |`MaFisRef("IT_BASEIV1","MT100",M->D2_BASIMP1)` |||N|||||
75|D2_SERIREM|C|3|0|Serie remito|Serie remito|`!!!` |||||||||
76|D2_BASIMP2|N|14|2|Base Imp. 2|Base de Calculo Imposto 2|`@E  99,999,999,999.99` |`MaFisRef("IT_BASEIV2","MT100",M->D2_BASIMP2)` |||N|||||
77|D2_BASIMP3|N|14|2|Base Imp. 3|Base de Calculo Imposto 3|`@E  99,999,999,999.99` |`MaFisRef("IT_BASEIV3","MT100",M->D2_BASIMP3)` |||N|||||
78|D2_ITEMREM|C|2|0|Item remito|Item remito|||||N|V||||
79|D2_BASIMP4|N|14|2|Base Imp. 4|Base de Calculo Imposto 4|`@E  99,999,999,999.99` |`MaFisRef("IT_BASEIV4","MT100",M->D2_BASIMP4)` |||N|||||
80|D2_BASIMP5|N|14|2|Base Imp. 5|Base de Calculo Imposto 5|`@E  99,999,999,999.99` |`MaFisRef("IT_BASECF2","MT100",M->D2_BASIMP5)` |||N|||||
81|D2_BASIMP6|N|14|2|Base Imp. 6|Base de Calculo Imposto 6|`@E  99,999,999,999.99` |`MaFisRef("IT_BASEPS2","MT100",M->D2_BASIMP6)` |||N|||||
82|D2_VALIMP1|N|14|2|Valor Imp. 1|Valor do Imposto 1|`@E  99,999,999,999.99` |`MaFisRef("IT_VALIV1","MT100",M->D2_VALIMP1)` |||N|||||
83|D2_VALIMP2|N|14|2|Valor Imp. 2|Valor do Imposto 2|`@E  99,999,999,999.99` |`MaFisRef("IT_VALIV2","MT100",M->D2_VALIMP2)` |||N|||||
84|D2_VALIMP3|N|14|2|Valor Imp. 3|Valor do Imposto 3|`@E  99,999,999,999.99` |`MaFisRef("IT_VALIV3","MT100",M->D2_VALIMP3)` |||N|||||
85|D2_VALIMP4|N|14|2|Valor Imp. 4|Valor do Imposto 4|`@E  99,999,999,999.99` |`MaFisRef("IT_VALIV4","MT100",M->D2_VALIMP4)` |||N|||||
86|D2_VALIMP5|N|14|2|Valor Imp. 5|Valor do Imposto 5|`@E  99,999,999,999.99` |`MaFisRef("IT_VALCF2","MT100",M->D2_VALIMP5)` |||N|||||
87|D2_VALIMP6|N|14|2|Valor Imp. 6|Valor do Imposto 6|`@E  99,999,999,999.99` |`MaFisRef("IT_VALPS2","MT100",M->D2_VALIMP6)` |||N|||||
88|D2_ITEMORI|C|4|0|It.Doc. Orig|Nr Item do Doc.original|`@!` |`Vazio() .Or. Iif(FindFunction("A920ItemOri"),  A920ItemOri(), .T. )` |||N|||||
89|D2_CODFAB|C|6|0|Fabricante|Codigo do Fabricante|`@!` |||SA1|N|V||||
90|D2_LOJAFA|C|2|0|Loja Fabric.|Loja do Fabricante|`@!` ||||N|V||||
91|D2_ALQIMP1|N|6|2|Aliq. Imp. 1|Aliquota do Imposto 1|`@E  999.99` |`MaFisRef("IT_ALIQIV1","MT100",M->D2_ALQIMP1)` ||||||||
92|D2_SERMAN|C|3|0|Série Manual|Série Doc. Manual|`!!!` ||||N|A|R|||
93|D2_ALQIMP2|N|6|2|Aliq. Imp. 2|Aliquota do Imposto 2|`@E  999.99` |`MaFisRef("IT_ALIQIV2","MT100",M->D2_ALQIMP2)` ||||||||
94|D2_ALQIMP3|N|6|2|Aliq. Imp. 3|Aliquota do Imposto 3|`@E  999.99` |`MaFisRef("IT_ALIQIV3","MT100",M->D2_ALQIMP3)` ||||||||
95|D2_ALQIMP4|N|6|2|Aliq. Imp. 4|Aliquota do Imposto 4|`@E  999.99` |`MaFisRef("IT_ALIQIV4","MT100",M->D2_ALQIMP4)` ||||||||
96|D2_ALQIMP5|N|6|2|Aliq. Imp. 5|Aliquota do Imposto 5|`@E  999.99` |`MaFisRef("IT_ALIQCF2","MT100",M->D2_ALQIMP5)` ||||||||
97|D2_ALQIMP6|N|6|2|Aliq. Imp. 6|Aliquota do Imposto 6|`@E  999.99` |`MaFisRef("IT_ALIQPS2","MT100",M->D2_ALQIMP6)` ||||||||
98|D2_ESPECIE|C|5|0|Especie|Especie|`@!` ||||N|||||
99|D2_CCUSTO|C|9|0|Centro Custo|Centro de Custo|`@!` |`Vazio() .Or. Ctb105CC()` ||CTT|N|||||
A0|D2_ITEMCC|C|9|0|Item C.C.|Item de Conta Contabil|`@!` |`Vazio() .Or. Ctb105Item()` ||CTD|N|||||
A1|D2_LOCALIZ|C|15|0|Endereco|Endereco do Lote|`@!` |||SBE|N|||||
A2|D2_ENVCNAB|D|8|0|Envio Cnab|Data do Envio do Cnab|||||N|||||
A3|D2_DFABRIC|D|8|0|Data Fabric.|Data de Fabricacao do Lot||`M->D2_DFABRIC<=DDATABASE` ||||||||
A4|D2_ABSCINS|N|14|2|Ab. INSS Sub|Abat. INSS Subcontrat.|`@E 999,999,999.99` |`MaFisRef("IT_ABSCINS","MT100",M->D2_ABSCINS)` ||||||||
A5|D2_ALIQINS|N|5|2|Aliq. INSS|Aliquota de INSS|`@E 99.99` |`MaFisRef("IT_ALIQINS","MT100",M->D2_ALIQINS)` |||N|||||
A6|D2_VLIMPOR|N|14|2|Vl.Import|Valor da Importação|`@E 99,999,999,999.99` |`Positivo()` |||S|A|R|||
A7|D2_VCAT156|N|16|2|V Tot CAT156|Valor Total CAT156|`@E 9,999,999,999,999.99` |||||||||
A8|D2_PREEMB|C|20|0|Proc.Embarq.|Proc.Embarq.Export.|`@!` ||||N|V||||
A9|D2_ALIQISS|N|5|2|Aliq. ISS|Aliquota de ISS|`@E 99.99` |`MaFisRef("IT_ALIQISS","MT100",M->D2_ALIQISS)` |||N|||||
B0|D2_BASEIPI|N|14|2|Vlr.Base IPI|Valor Base de Calc. IPI|`@E 99,999,999,999.99` |`Positivo().And.MaFisRef("IT_BASEIPI","MT100",M->D2_BASEIPI)` |||N|||||
B1|D2_BASEISS|N|14|2|Base de ISS|Base de calculo do ISS|`@E 999,999,999.99` |`MaFisRef("IT_BASEISS","MT100",M->D2_BASEISS)` |||N|||||
B2|D2_VALISS|N|14|2|Valor do ISS|Valor do ISS|`@E 999,999,999.99` |`MaFisRef("IT_VALISS","MT100",M->D2_VALISS)` |||N|||||
B3|D2_SEGURO|N|14|2|Vlr. Seguro|Valor do Seguro do item|`@E 99,999,999.99` |`MaFisRef("IT_SEGURO","MT100",M->D2_SEGURO)` |||N|||||
B4|D2_VALFRE|N|14|2|Vlr. Frete|Valor do Frete|`@E 999,999,999.99` |`MaFisRef("IT_FRETE","MT100",M->D2_VALFRE)` |||N|||||
B5|D2_TPDCENV|C|1|0|Tipo env ori|Tipo envio original|||||N||||`.F.` |
B6|D2_DESPESA|N|14|2|Vlr. Despesa|Valor das Despesas|`@E 99,999,999.99` |`MaFisRef("IT_DESPESA","MT100",M->D2_DESPESA)` |||N|||||
B7|D2_OK|C|2|0|Marca|Marca||||||||||
B8|D2_CLVL|C|9|0|Classe Valor|Classe Valor Contabil|`@!` |`Vazio() .Or. Ctb105ClVl()` ||CTH|N||||`CtbInUse()` |
B9|D2_CODGRP|C|4|0|Grupo|Grupo Veiculos/Oficina|`@!!!!` |`VldAuxCod1("D2_CODGRP","D2_CODITE")` |IniAuxCod(SD2->D2_COD,"D2_CODGRP")|SBM|N||V|||
C0|D2_CODITE|C|27|0|Cod. Produto|Produto Veiculos/Oficina||`VldAuxCod2("D2_COD","D2_CODGRP")` |IniAuxCod(SD2->D2_COD,"D2_CODITE")|B00|N||V|||
C1|D2_BASEINS|N|14|2|Base de INSS|Base de calculo do INSS|`@E 999,999,999.99` |`MaFisRef("IT_BASEINS","MT100",M->D2_BASEINS)` |||N|||||
C2|D2_ICMFRET|N|14|2|Icms Frete|Icms Frete|`@E 99,999,999.99` |||||||||
C3|D2_SERVIC|C|3|0|Cod.Servico|Codigo do Servico|`@!` |`ExistCpo('DC5')` ||DC5|N|||||
C4|D2_STSERV|C|1|0|Status Serv.|Status do Servico|`@!` |`Pertence('123')` |'1'||N|V||1=Servico Nao Executado;2=Servico Interrompido;3=Servico Executado||
C5|D2_VALINS|N|14|2|Vlr. do INSS|Valor do INSS|`@E 999,999,999.99` |`MaFisRef("IT_VALINS","MT100",M->D2_VALINS)` |||N|||||
C6|D2_PROJPMS|C|10|0|Cod.Projeto|Codigo do Projeto||`Vazio().Or.ExistCpo("AF8")` ||AF8|N|||||
C7|D2_EDTPMS|C|12|0|EDT|Codigo da EDT|`@!` |`Vazio() .Or. A410VldPrj()` ||AFC|N||||`PmsSetF3("AFC",9)` |
C8|D2_TASKPMS|C|12|0|Cod.Tarefa|Codigo da Tarefa|`@!` |`Vazio().Or.A410VldPrj()` ||AF9|N||||`PmsSetF3("AF9",9)` |
C9|D2_LICITA|C|6|0|Cod.Licitac.|Codigo da licitacao|`@!` |`Vazio().Or.ExistCpo("AH9")` ||AH9|N|||||
D0|D2_VARPRUN|N|9|2|Var.Prc.Unit|Variacao do Preco Unit.|`@E 999,999.99` ||||N|||||
D1|D2_FORMUL|C|1|0|Form. Prop.|Formulario Proprio|`!` ||||N|||||
D2|D2_TIPODOC|C|2|0|Id. Doc.|Identificador de doc.|||||N|||||
D3|D2_VAC|N|14|2|Ac. Creditar|Acrescimo a Creditar|`@E 999,999,999.99` ||||N|||||
D4|D2_TIPOREM|C|1|0|Tipo Envio|Tipo Envio|||||N||||`.F.` |
D5|D2_QTDEFAT|N|16|4|Quant.Fatur.|Quantidade ja faturada|`@E 99,999,999,999.9999` ||||S|||||
D6|D2_QTDAFAT|N|16|4|Quant. a Fat|Quantidade a faturar|`@E 99,999,999,999.9999` ||||S|||||
D7|D2_SEQUEN|C|2|0|Sequência|Sequencia|`99` |||||||||
D8|D2_POTENCI|N|6|2|Potencia|Potencia de Lote|`@E 999.99` |||||V||||
D9|D2_TPESTR|C|6|0|Estr.Fisica|Cod. da Estrutura Fisica|`@!` |`ExistCpo("DC8")` ||DC8|S|||||
E0|D2_VALBRUT|N|14|2|Vlr.Bruto|Valor Bruto do Item|`@E 99,999,999,999.99` |`MaFisRef("IT_TOTAL","MT100",M->D2_VALBRUT)` ||||V||||
E1|D2_REGWMS|C|1|0|Regra WMS|Regra de apanhe do WMS|`9` |`Pertence("123")` ||||||1=Lote;2=Numero de Serie;3=Data||
E2|D2_DTDIGIT|D|8|0|Data Digit.|Data de digitacao|||||N|V|R|||
E3|D2_NUMCP|C|6|0|Comp. Fut.|Compromisso Futuro||`Vazio() .Or. ExistCpo("NO1")` |||N|A|R|||
E4|D2_CUSRP1|N|14|2|C Reposicao|Custo de Reposicao|`@E 999,999,999.99` ||||N|||||
E5|D2_CUSRP2|N|14|2|C Repos.2a M|Custo de Reposicao 2a M|`@E 999,999,999.99` ||||N|||||
E6|D2_CUSRP3|N|14|2|C Repos.3a M|Custo de Reposicao 3a M|`@E 999,999,999.99` ||||N|||||
E7|D2_CUSRP4|N|14|2|C Repos.4a M|Custo de Reposicao 4a M|`@E 999,999,999.99` ||||N|||||
E8|D2_CUSRP5|N|14|2|C Repos.5a M|Custo de Reposicao 5a M|`@E 999,999,999.99` ||||N|||||
E9|D2_SITTRIB|C|5|0|Aliquota|Situacao Tributaria ECF|||||N|A||||
F0|D2_NFCUP|C|9|0|Num. NF/CUP|Numero da Nota ou Cupom|`@!` ||||N|A|R|||
F1|D2_OKISS|C|10|0|Amarrac. Iss|Amarracao NF Saida ao Ped|`@!` ||||N|A|R|||
F2|D2_MSEXP|C|8|0|Ident.Exp.|Ident.Exp.Dados|||||N|V|R|||
F3|D2_IDCFC|C|20|0|ID Hist. CFC|ID Histórico CFC|`@` |`MaFisRef("IT_IDCFC","MT100",M->D2_IDCFC)` |||N|V|R|||
F4|D2_IDSB1|C|20|0|ID Hist. SB1|ID Hist. SB1|`@!` |`MaFisRef("IT_IDSB1","MT100",M->D2_IDSB1)` |||N||R|||
F5|D2_IDSB5|C|20|0|ID Hist. SB5|ID Hist. SB5|`@!` |`MaFisRef("IT_IDSB5","MT100",M->D2_IDSB5)` |||N||R|||
F6|D2_IDSBZ|C|20|0|ID Hist. SBZ|ID Hist. SBZ|`@!` |`MaFisRef("IT_IDSBZ","MT100",M->D2_IDSBZ)` |||N||R|||
F7|D2_IDSF4|C|20|0|ID Hist. SF4|ID Hist. SF4|`@!` |`MaFisRef("IT_IDSF4","MT100",M->D2_IDSF4)` |||N||R|||
F8|D2_IDSF7|C|20|0|ID Hist. SF7|ID Hist. SF7|`@!` |`MaFisRef("IT_IDSF7","MT100",M->D2_IDSF7)` |||N||R|||
F9|D2_INDICE|N|16|4|Indicador|Indicador Econômico|`@E 99,999,999,999.9999` |`MaFisRef("IT_INDICE","MT100",M->D2_INDICE)` |||S|A|R|||
G0|D2_PRFDSUL|N|12|8|Pr.Fundersul|Percentual Fundersul|`@E 999.9999999` |`MaFisRef("IT_PRFDSUL","MT100",M->D2_PRFDSUL)` |||N|A|R|||
G1|D2_ORDSEP|C|6|0|Ordem Sep.|Ordem de Separacao|||||N|V|R|||
G2|D2_PRUNDA|N|14|2|Vlr Unit DA|Valor Unitario D. A.|`@E 999,999,999.99` |||||||||
G3|D2_CODROM|C|6|0|Cod Romaneio|Codigo do Romaneio|`@!` |||NPR|N|A|R|||
G4|D2_CNATREC|C|3|0|Cod.Nat.Rec.|Código Nat. Receita|`@!` |`MAFISREF("IT_CODNTRE","MT100",M->D2_CNATREC)` |||N|V|R|||
G5|D2_CFPS|C|6|0|Cod. CFPS|Código CFPS|`@9` |`MaFisRef("IT_CFPS","MT100",M->D2_CFPS)` ||||||||
G6|D2_BASFEEF|N|14|2|Bas.FEEF.RJ|Base FEEF-RJ|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("IT_BASFEEF","MT100",M->D2_BASFEEF)` |||N|||||
G7|D2_DTFIMNT|D|8|0|Dt.Fim N.R.|Dt.Fim Nat.Receita||`MAFISREF("IT_DATNTRE","MT100",M->D1_DTFIMNT)` |||N|V|R|||
G8|D2_DESCZFC|N|14|2|Val.Cof.ZFM|Val. desc. COF para ZFM|`@E 99,999,999,999.99` |`MaFisRef("IT_DESCZFCOF","MT100",M->D2_DESCZFC)` |||N|A|R|||
G9|D2_DESCZFP|N|14|2|Val.Pis.ZFM|Val. desc. do PIS para ZF|`@E 99,999,999,999.99` |`MaFisRef("IT_DESCZFPIS","MT100",M->D2_DESCZFP)` |||N|A|R|||
H0|D2_CRPRESC|N|14|2|Crd Pres SC|Crd Presumido - SC|`@E 99,999,999,999.99` |`MaFisRef("IT_CRPRESC","MT100",M->D2_CRPRESC)` |||N|A|R|||
H1|D2_DESCICM|N|14|2|Ded.ICMS|Deducao do ICM do Item|`@E 99,999,999,999.99` |`MaFisRef("IT_DEDICM","MT100",M->D2_DESCICM)` |||S|V|R|||
H2|D2_FTRICMS|N|8|5|Fat.Desc.ICM|Fator de Redução Desc.ICM|`@E 99.99999` |`MaFisRef("IT_FTRICMS","MT100",M->D2_FTRICMS)` |||N|A|R|||
H3|D2_GRPCST|C|3|0|Enq. IPI|Cod. Enquadramento do IPI|`@!` |`MaFisRef("IT_GRPCST","MT100",M->D2_GRPCST)` ||||||||
H4|D2_GRUPONC|C|2|0|Grp.Nat.Rec.|Grupo Natureza da Receita|`@!` |`MAFISREF("IT_GRPNTRE","MT100",M->D2_GRUPONC)` |||N|V|R|||
H5|D2_HREXPO|C|8|0|Hr. Ult. Exp|Hora da Ultima Exportação|||||N|V|R|||
H6|D2_CTAREC|C|20|0|Cta Receita|Conta Receita|`@!` |`Vazio() .Or. Ctb105Cta()` ||CT1||V|R|||
H7|D2_ESTCRED|N|16|2|Vlr Est Deb|Valor Estorno Débito|`@E 9,999,999,999,999.99` |`MaFisRef("IT_ESTCRED","MT100",M->D2_ESTCRED)` |||N|A|R|||
H8|D2_ESTOQUE|C|1|0|Mov Estoque|Movimenta Estoque|`@!` |`pertence("SN")` |||N|V|R|S=Sim;N=Nao||
H9|D2_FCICOD|C|36|0|Codigo FCI|Codigo FCI|`@!` ||||N|V|R|||
I0|D2_ALIQINA|N|5|2|Aliq INSS Ad|Aliquota do INSS Condiçõe|`@E 99.99` |`MaFisRef("IT_ALIQINA","MT100",M->D2_ALIQINA)` |||N|A|R|||
I1|D2_BASEINA|N|14|2|Base INSS Ad|Base do INSS Condições Es|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEINA","MT100",M->D2_BASEINA)` |||N|A|R|||
I2|D2_BASEIRR|N|16|2|Base IR|Valor da Base do IR|`@E 9,999,999,999,999.99` |`MaFisRef("IT_BASEIRR","MT100",M->D2_BASEIRR)` |||N|A|R|||
I3|D2_BASEPIS|N|14|2|Base Pis|Base do PIS|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEPIS","MT100",M->D2_BASEPIS)` ||||||||
I4|D2_BASEPS3|N|14|2|Bs. Pis ST|Base Pis ST|`@E 99,999,999,999.99` |`Positivo().And.MaFisRef("IT_BASEPS3","MT100",M->D2_BASEPS3)` |||N|||||
I5|D2_BASETST|N|14|2|Base ST tran|Base ICMS ST transporte|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("IT_BASETST","MT100",M->D2_BASETST)` |||N|A|R|||
I6|D2_ALQIRRF|N|6|2|Aliq. IRRF|Aliquota do IRRF|`@E 999.99` |`MaFisRef("IT_ALIQIRR","MT100",M->D2_ALQIRRF)` ||||||||
I7|D2_BASECF3|N|14|2|Bs. Cof ST|Base Cofins ST|`@E 99,999,999,999.99` |`Positivo().And.MaFisRef("IT_BASECF3","MT100",M->D2_BASECF3)` |||N|||||
I8|D2_BASECOF|N|14|2|Base Cofins|Base do Cofins|`@E 99,999,999,999.99` |`MaFisRef("IT_BASECOF","MT100",M->D2_BASECOF)` ||||||||
I9|D2_BASECPM|N|14|2|Bs.ISS CPM|Base ISS CPM|`@E 99,999,999,999.99` |`MaFisRef("IT_BASECPM","MT100",M->D2_BASECPM)` ||||||||
J0|D2_BASECSL|N|14|2|Base CSLL|Base do CSLL|`@E 99,999,999,999.99` |`MaFisRef("IT_BASECSL","MT100",M->D2_BASECSL)` ||||||||
J1|D2_BASEFAB|N|14|2|Base Fabov|Base do Fabov|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEFAB","MT100",M->D2_BASEFAB)` |||N|A|R|||
J2|D2_BASEFAC|N|14|2|Base Facs|Base do Facs|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEFAC","MT100",M->D2_BASEFAC)` |||N|A|R|||
J3|D2_BASEFET|N|14|2|Base Fethab|Base do Fethab|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEFET","MT100",M->D2_BASEFET)` |||N|A|R|||
J4|D2_BASEFMD|N|14|2|Base Famad|Base do Famad|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEFMD","MT100",M->D2_BASEFMD)` ||||||||
J5|D2_BASEFMP|N|14|2|Base FUMIPEQ|Base de Cálculo FUMIPEQ|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEFMP","MT100",M-> D2_BASEFMP)` ||||||||
J6|D2_ALIQCF3|N|5|2|Al. Cof ST|Aliquota Cofins ST|`@E 99.99` |`Positivo().And.MaFisRef("IT_ALIQCF3","MT100",M->D2_ALIQCF3)` |||N|||||
J7|D2_ALIQCPB|N|5|2|Alíquota CPR|Alíquota da CPRB|`@E 99.99` |`Positivo() .And. MaFisRef("IT_ALIQCPB","MT100",M->D2_ALIQCPB)` |||S|||||
J8|D2_ALIQFAB|N|5|2|Aliq. Fabov|Aliquota do Fabov|`@E 99.99` |`MaFisRef("IT_ALIQFAB","MT100",M->D2_ALIQFAB)` |||N|A|R|||
J9|D2_ALIQFAC|N|5|2|Aliq. Facs|Aliquota do Facs|`@E 99.99` |`MaFisRef("IT_ALIQFAC","MT100",M->D2_ALIQFAC)` |||N|A|R|||
K0|D2_ALIQFET|N|5|2|Aliq. Fethab|Aliquota do Fethab|`@E 99.99` |`MaFisRef("IT_ALIQFET","MT100",M->D2_ALIQFET)` |||N|A|R|||
K1|D2_ALIQPS3|N|5|2|Al. Pis ST|Aliquota Pis ST|`@E 99.99` |`Positivo().And.MaFisRef("IT_ALIQPS3","MT100",M->D2_ALIQPS3)` |||N|||||
K2|D2_ALIQSOL|N|6|2|Alq ICMS Sol|Aliq. ICMS Sol.|`@E 999.99` |`MaFisRef("IT_ALIQSOL","MT100",M->D2_ALIQSOL)` |||S|||||
K3|D2_ALIQTST|N|5|2|Aliq ST tran|Aliq. ICMS ST transporte|`@E 99.99` |`Positivo() .And. MaFisRef("IT_ALIQTST","MT100",M->D2_ALIQTST)` |||N|A|R|||
K4|D2_ALQCPM|N|5|2|Alq.ISS CPM|Alíquota ISS CPM|`@E 99.99` |`MaFisRef("IT_ALQCPM","MT100",M->D2_ALQCPM)` ||||||||
K5|D2_ALQFEEF|N|5|2|Aliq.FEEF.RJ|Alíquota FEEF-RJ|`@E 99.99` |`Positivo() .And. MaFisRef("IT_ALQFEEF","MT100",M->D2_ALQFEEF)` |||N|||||
K6|D2_ALQFMD|N|5|2|Aliq. Famad|Alíquota do Famad|`@E 99.99` |`MaFisRef("IT_ALQFMD","MT100",M->D2_ALQFMD)` ||||||||
K7|D2_ALQFMP|N|5|2|Aliq. FUMIPE|Aliquota de FUMIPEQ|`@E 99.99` |`MaFisRef("IT_ALQFMP","MT100",M-> D2_ALQFMP)` ||||||||
K8|D2_09CAT17|N|14|2|Col.09 Cat17|Coluna 09 da Cat17|`@E 99,999,999,999.99` ||||S|A|R|||
K9|D2_16CAT17|N|14|2|Col.16 Cat17|Coluna 16 da Cat17|`@E 99,999,999,999.99` ||||S|A|R|||
L0|D2_ABATINS|N|14|2|Abatim. INSS|Valor abatimento / INSS|`@E 99,999,999,999.99` |`MaFisRef("IT_ABVLINSS","MT100",M->D2_ABATINS)` |||N|A|R|||
L1|D2_ABATISS|N|14|2|Abatim. ISS|Valor abatimento / ISS|`@E 99,999,999,999.99` |`MaFisRef("IT_ABVLISS","MT100",M->D2_ABATISS)` |||N|A|R|||
L2|D2_ABATMAT|N|14|2|Abat. Mat.|Abatimento ISS material|`@E 99,999,999,999.99` |`MaFisRef("IT_ABMATISS","MT100",M->D2_ABATMAT)` |||N|A|R|||
L3|D2_TNATREC|C|4|0|Tab.Nat.Rec.|Tab. Nat. Receita|`@!` |`MAFISREF("IT_TABNTRE","MT100",M->D2_TNATREC)` |||N|V|R|||
L4|D2_TOTEST|N|14|2|Crg.Trb.Est|Carga Tributária Estadual|`@E 99,999,999,999.99` ||||N|A|R|||
L5|D2_TOTFED|N|14|2|Crg.Trb.Fed|Carga Tributária Federal|`@E 99,999,999,999.99` ||||N|A|R|||
L6|D2_TOTIMP|N|14|2|Perc.Cg.Trb|Percentual Carga Tributa|`@E 99,999,999,999.99` ||||N|A|R|||
L7|D2_TOTMUN|N|14|2|Crg.Trb.Mun|Carga Tributária Municipa|`@E 99,999,999,999.99` ||||N|A|R|||
L8|D2_VALCF3|N|14|2|Vl. Cof ST|Valor Cofins ST|`@E 99,999,999,999.99` |`Positivo().And.MaFisRef("IT_VALCF3","MT100",M->D2_VALCF3)` |||N|||||
L9|D2_VALCOF|N|14|2|Valor Cofins|Valor do Cofins|`@E 99,999,999,999.99` |`MaFisRef("IT_VALCOF","MT100",M->D2_VALCOF)` ||||||||
M0|D2_VALCPB|N|14|2|Valor CPRB|Valor da CPRB|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("IT_VALCPB","MT100",M->D2_VALCPB)` |||S|||||
M1|D2_VALCPM|N|14|2|Vl.ISS CPM|Valor ISS CPM|`@E 99,999,999,999.99` |`MaFisRef("IT_VALCPM","MT100",M->D2_VALCPM)` ||||||||
M2|D2_VALFAB|N|14|2|Vlr. Fabov|Valor do Fabov|`@E 99,999,999,999.99` |`MaFisRef("IT_VALFAB","MT100",M->D2_VALFAB)` |||N|A|R|||
M3|D2_VALFAC|N|14|2|Vlr. Facs|Valor do Facs|`@E 99,999,999,999.99` |`MaFisRef("IT_VALFAC","MT100",M->D2_VALFAC)` |||N|A|R|||
M4|D2_TRT|C|3|0|Seq. Empenho|Sequencia do Empenho|`@!` |`Vazio()` |||S|A|R||`.F.` |
M5|D2_UFERMS|N|14|2|UFERMS|Valor UFERMS|`@E 999,999,999.99` |`MaFisRef("IT_UFERMS","MT100",M->D2_UFERMS)` |||N|A|R|||
M6|D2_VALIRRF|N|14|2|Valor IRRF|Valor do IRRF|`@E 99,999,999,999.99` |`MaFisRef("IT_VALIRR","MT100",M->D2_VALIRRF)` ||||||||
M7|D2_VALPS3|N|14|2|Vl. Pis ST|Valor Pis ST|`@E 99,999,999,999.99` |`Positivo().And.MaFisRef("IT_VALPS3","MT100",M->D2_VALPS3)` |||N|||||
M8|D2_VALTST|N|14|2|Val. ST tran|Valor ICMS ST transporte|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("IT_VALTST","MT100",M->D2_VALTST)` |||N|A|R|||
M9|D2_VALFDS|N|14|2|Vl.Fundersul|Valor do Fundersul|`@E 999,999,999.99` |`MaFisRef("IT_VALFDS","MT100",M->D2_VALFDS)` |||N|A|R|||
N0|D2_VALFEEF|N|14|2|Val.FEEF.RJ|Valor do FEEF-RJ|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("IT_VALFEEF","MT100",M->D2_VALFEEF)` |||N|||||
N1|D2_VALFET|N|14|2|Vlr. Fethab|Valor do Fethab|`@E 99,999,999,999.99` |`MaFisRef("IT_VALFET","MT100",M->D2_VALFET)` |||N|A|R|||
N2|D2_VALFMD|N|14|2|Vlr. Famad|Valor do Famad|`@E 99,999,999,999.99` |`MaFisRef("IT_VALFMD","MT100",M->D2_VALFMD)` ||||||||
N3|D2_VALFMP|N|14|2|Vl. FUMIPEQ|Valor do FUMIPEQ|`@E 99,999,999,999.99` |`MaFisRef("IT_VALFMP","MT100",M->D2_VALFMP)` ||||||||
N4|D2_VALINA|N|14|2|Vlr INSS Ad|Valor do INSS Condições E|`@E 99,999,999,999.99` |`MaFisRef("IT_VALINA","MT100",M->D2_VALINA)` |||N|A|R|||
N5|D2_VRDICMS|N|16|2|Val.Desc.ICM|Valor de Redução Desc.ICM|`@E 9,999,999,999,999.99` |`MaFisRef("IT_VRDICMS","MT100",M->D2_VRDICMS)` |||N|A|R|||
N6|D2_CODLAN|C|6|0|Cod. CAT83|Codigo CAT/83|`@!` |`Vazio() .Or. ExistCpo('CDZ')` ||||||||
N7|D2_CODLPRE|C|6|0|Lista Pres.|Lista de Presentes|`@!` ||||S||R|||
N8|D2_BASFUND|N|14|2|Base FUNDESA|Base do FUNDESA|`@E 99,999,999,999.99` |`MaFisRef("IT_BASFUND","MT100",M->D2_BASFUND)` |||S|A|R|||
N9|D2_BASIMA|N|14|2|Base IMA-MT|Base do IMA-MT|`@E 99,999,999,999.99` |`MaFisRef("IT_BASIMA","MT100",M->D2_BASIMA)` |||S|A|R|||
O0|D2_BSFCCMP|N|14|2|Base FCP Cmp|Base FCP Complementar|`@E 99,999,999,999.99` |`MaFisRef("IT_BSFCCMP","MT100",M->D2_BSFCCMP)` |||S|A|R|||
O1|D2_BSFCPST|N|14|2|Base FCP ST|Base FCP ST|`@E 99,999,999,999.99` |`MaFisRef("IT_BSFCPST","MT100",M->D2_BSFCPST)` |||S|A|R|||
O2|D2_BSREIN|N|14|2|B.C.Reinteg|Base Calc.Reintegra|`@E 99,999,999,999.99` |`'MaFisRef("IT_BSREIN","MT100",M->D2_BSREIN)'` |||S|A|R|||
O3|D2_BSSENAR|N|14|2|Base Seanr|Base do Senar|`@E 99,999,999,999.99` |`MaFisRef("IT_BSSENAR","MT100",M->D2_BSSENAR)` |||S|A|R|||
O4|D2_CBASEAF|C|14|0|Imobilizado|Numero do imobilizado|`@!` ||||N||R|||
O5|D2_FCPAUX|N|7|4|Ind.Fcp.Aux.|Indice Auxiliar do FCP|`@E 99.9999` |`MaFisRef("IT_FCPAUX","MT100",M->D2_FCPAUX)` |||S|A|R|||
O6|D2_CSOSN|C|3|0|Cód Sit SN|Cód Sit Ope SN|`@!` |`MaFisRef("IT_CSOSN","MT100",M->D2_CSOSN)` |||S|A|R|||
O7|D2_DECQTD|N|1|0|Dec. Qtde|Dec. Qtde|`9` |||||A|R|||
O8|D2_DECVLU|N|1|0|Dec. VlUN|Dec. Vl Unitário|`9` |||||A|R|||
O9|D2_DIFAL|N|14|2|ICMS Difal|ICMS Comple. UF Destino|`@E 99,999,999,999.99` |`MaFisRef("IT_DIFAL","MT100",M->D2_DIFAL)` |||S|A|R|||
P0|D2_REVISAO|C|3|0|Revisão|Revisão do produto|||||N|A|R|||
P1|D2_SDOC|C|3|0|Série Doc.|Série do Documento Fiscal|`!!!` ||||N|V|R|||
P2|D2_SDOCMAN|C|3|0|Série Manual|Série Doc. Manual|`!!!` ||||N|V|R|||
P3|D2_SDOCORI|C|3|0|Série Orig.|Série da N.F. Original|`!!!` ||||N|V|R|||
P4|D2_SDOCREM|C|3|0|Série Doc.|Série do Documento Fiscal|`!!!` ||||N|V|R|||
P5|D2_RATEIO|C|1|0|Rateio|Rateio|`@!` ||'2'|||||1=Sim;2=Nao||
P6|D2_ORCGAR|C|6|0|Orca Gar Est|Orcamento Garantia Estend|`@!` ||||N|A|R|||
P7|D2_PAFMD5|C|32|0|MD5|Chave MD5 do Registro||||||A|R|||
P8|D2_PDDES|N|6|2|Perc. Destin|Perc. Difal Destino|`@E 999.99` |`MaFisRef("IT_PDDES","MT100",M->D2_PDDES)` |||S|A|R|||
P9|D2_PDORI|N|6|2|Perc. Origem|Perc. Difal Origem|`@E 999.99` |`MaFisRef("IT_PDORI","MT100",M->D2_PDORI)` |||S|A|R|||
Q0|D2_PRINCMG|N|6|2|Pr.Inc.Leite|Perc.Incentivo Prod.Leite|`@E 999.99` |`MAFISREF("IT_PRINCMG","MT100",M->D2_PRINCMG)` |||N|V||||
Q1|D2_PRODFIN|C|15|0|Prod Final|Produto Final|`@!` |`Vazio() .or. ExistCPO("SB1")` ||SB1||||||
Q2|D2_ITEMGAR|C|2|0|Item Gar Est|Item Garantia Estendida|||||N|A|R|||
Q3|D2_ITLPRE|C|3|0|Item L.Pres.|Item da Lista de Presente|`@!` ||||S||R|||
Q4|D2_IDTRIB|C|36|0|Id. Tributos|ID de tributos|`@!` ||||N|V|R|||
Q5|D2_ICMSCOM|N|14|2|ICMS Comple.|Valor ICMS Complementar|`@E 99,999,999,999.99` |`MaFisRef("IT_VALCMP","MT100",M->D2_ICMSCOM)` |||S|A|R|||
Q6|D2_ICMSDIF|N|16|2|Vlr.ICMS Dif|Valor do ICMS Diferido|`@E 9,999,999,999,999.99` |`Positivo().And.MaFisRef("IT_ICMSDIF","MT100",M->D2_ICMSDIF)` |||S|A|R|||
Q7|D2_MARGEM|N|6|2|Solid. Saida|% Lucro Calc. Solid.Saida|`@E 999.99` |`Mafisref("IT_MARGEM","MT100",M->D2_MARGEM)` ||||A|R|||
Q8|D2_NRECAGR|C|5|0|Num Rec Agro|Num Receita Agronômica|`@!` ||||N|A|R|||
Q9|D2_ALFCCMP|N|6|2|FECP Comp.|FECP ICMS complementar|`@E 999.99` |`MaFisRef("IT_ALFCCMP","MT100",M->D2_ALFCCMP)` |||S|A|R|||
R0|D2_ALFCPST|N|6|2|Aliq. FCP ST|Alíquota do FCP ST|`@E 999.99` |`MaFisRef("IT_ALFCST","MT100",M->D2_ALFCPST)` |||S|A|R|||
R1|D2_ALIFASE|N|5|2|Aliq.FASE-MT|Alíquota do FASE-MT|`@E 99.99` |`MaFisRef("IT_ALIFASE","MT100",M->D2_ALIFASE)` |||S|A|R|||
R2|D2_ALIFUND|N|5|2|Aliq.FUNDESA|Alíquota do FUNDESA|`@E 99.99` |`MaFisRef("IT_ALIFUND","MT100",M->D2_ALIFUND)` |||S|A|R|||
R3|D2_ALIIMA|N|5|2|Aliq. IMA-MT|Alíquota do IMA-MT|`@E 99.99` |`MaFisRef("IT_ALIIMA","MT100",M->D2_ALIIMA)` |||S|A|R|||
R4|D2_ALQCSL|N|6|2|Aliq. CSLL|Aliquota CSLL|`@E 999.99` |`MaFisRef("IT_ALIQCSL","MT100",M->D2_ALQCSL)` ||||||||
R5|D2_ALQFECP|N|6|2|Aliq. FECP|Alíquota do FECP|`@E 999.99` |`MaFisRef("IT_ALIQFECP","MT100",M->D2_ALQFECP)` |||S|A|R|||
R6|D2_ALMTERC|C|2|0|Armz Terc.|Armazem de Terceiros|`@!` |`IsAlmTerc(M->D2_ALMTERC)` |||N|||||
R7|D2_ALQCOF|N|6|2|Aliq. Cofins|Aliquota do Cofins|`@E 999.99` |`MaFisRef("IT_ALIQCOF","MT100",M->D2_ALQCOF)` ||||||||
R8|D2_ALIQFUN|N|5|2|Alq FUNRURAL|Aliquota o FUNRURAL|`@E 99.99` |`MaFisRef("IT_PERFUN","MT100",M->D2_ALIQFUN)` |||N|V|R|||
R9|D2_ALIQCMP|N|6|2|Aliq Comp.|Aliq. ICMS complementar|`@E 999.99` |`MaFisRef("IT_ALIQCMP","MT100",M->D2_ALIQCMP)` |||S|A|R|||
S0|D2_ALIQPRO|N|5|2|Aliq.PROT.GO|Aliquota PROTEGE-GO|`@E 99.99` |`Positivo().And. MaFisRef("IT_ALIQPRO","MT100",M->D1_ALIQPRO)` ||||||||
S1|D2_BASEFUN|N|14|2|Bas FUNRURAL|Base de Calculo FUNRURAL|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEFUN","MT100",M->D2_BASEFUN)` |||N|V|R|||
S2|D2_BASEDES|N|14|2|Base. Destin|Base. Difal Destino|`@E 99,999,999,999.99` |`MaFisRef("IT_BASEDES","MT100",M->D2_BASEDES)` |||S|A|R|||
S3|D2_BASECPB|N|14|2|Base CPRB|Base da CPRB|`@E 99,999,999,999.99` |`Positivo() .And. MaFisRef("IT_BASECPB","MT100",M->D2_BASECPB)` |||S|||||
S4|D2_ALQPIS|N|6|2|Aliq. Pis|Aliquota do PIS|`@E 999.99` |`MaFisRef("IT_ALIQPIS","MT100",M->D2_ALQPIS)` ||||||||
S5|D2_ALSENAR|N|5|2|Aliq.Senar|Aliquota do Senar|`@E 99.99` |`MaFisRef("IT_ALSENAR","MT100",M->D2_ALSENAR)` |||N|A|R|||
S6|D2_BASFASE|N|14|2|Base FASE-MT|Base do FASE-MT|`@E 99,999,999,999.99` |`MaFisRef("IT_BASFASE","MT100",M->D2_BASFASE)` |||S|A|R|||
S7|D2_BASFECP|N|14|2|Base FCP Pr.|Base FCP Próprio|`@E 99,999,999,999.99` |`MaFisRef("IT_BASFECP","MT100",M->D2_BASFECP)` |||S|A|R|||
S8|D2_BASEPRO|N|14|2|Bas.PROT.GO|Base PROTEGE-GO|`@E 99,999,999,999.99` |`Positivo().And. MaFisRef("IT_BASEPRO","MT100",M->D1_BASEPRO)` ||||||||
S9|D2_VREINT|N|14|2|V.Reintegra|Valor Reintegra|`@E 99,999,999,999.99` |`'MaFisRef("IT_VREINT","MT100",M->D2_VREINT)'` |||S|A|R|||
T0|D2_VFCPDIF|N|14|2|Valor FECP|FECP da UF de destino|`@E 99,999,999,999.99` |`MaFisRef("IT_VFCPDIF","MT100",M->D2_VFCPDIF)` |||S|A|R|||
T1|D2_VFECPST|N|14|2|Vlr FCP ST|Valor do FCP ST|`@E 99,999,999,999.99` |`MaFisRef("IT_VFECPST","MT100",M->D2_VFECPST)` |||S|A|R|||
T2|D2_VALFECP|N|14|2|Vlr FCP Prop|Valor do FCP Próprio|`@E 99,999,999,999.99` |`MaFisRef("IT_VALFECP","MT100",M->D2_VALFECP)` |||S|A|R|||
T3|D2_VALPIS|N|14|2|Valor Pis|Valor do Pis|`@E 99,999,999,999.99` |`MaFisRef("IT_VALPIS","MT100",M->D2_VALPIS)` ||||||||
T4|D2_VALPRO|N|14|2|Val.PROT.GO|Valor do PROTEGE-GO|`@E 99,999,999,999.99` |`Positivo().And. MaFisRef("IT_VALPRO","MT100",M->D1_VALPRO)` ||||||||
T5|D2_VLINCMG|N|14|2|Vl.Inc.Leite|Vl.Incentivo Prod.Leite|`@E 99,999,999,999.99` |`MAFISREF("IT_VLINCMG","MT100",M->D2_VLINCMG)` |||N|V||||
T6|D2_VLSENAR|N|14|2|Valor Senar|Valor do Senar|`@E 99,999,999,999.99` |`MaFisRef("IT_VLSENAR","MT100",M->D2_VLSENAR)` |||N|A|R|||
T7|D2_VOPDIF|N|16|2|Vlr.OP.Dif|Valor da Operação|`@E 9,999,999,999,999.99` |`Positivo().And.MaFisRef("IT_VOPDIF","MT100",M->D2_VOPDIF)` |||S|A|R|||
T8|D2_VALFUN|N|14|2|Vlr FUNRURAL|Valor do FUNRURAL|`@E 99,999,999,999.99` |`MaFisRef("IT_FUNRURAL","MT100",M->D2_VALFUN)` |||N|V|R|||
T9|D2_VALFUND|N|14|2|Vlr.FUNDESA|Valor do FUNDESA|`@E 99,999,999,999.99` |`MaFisRef("IT_VALFUND","MT100",M->D2_VALFUND)` |||S|A|R|||
U0|D2_VALIMA|N|16|2|Vlr. IMA-MT|Valor do IMA-MT|`@E 9,999,999,999,999.99` |`MaFisRef("IT_VALIMA","MT100",M->D2_VALIMA)` |||S|A|R|||
U1|D2_TPREPAS|C|6|0|Tipo Repasse|Tipo de Repasse|`@!` |`Vazio() .OR. ExistCpo("SX5","0G"+M->D2_TPREPAS)` ||0G||A|R|||
U2|D2_VALFASE|N|14|2|Vlr.FASE-MT|Valor do FASE-MT|`@E 99,999,999,999.99` |`MaFisRef("IT_VALFASE","MT100",M->D2_VALFASE)` |||S|A|R|||


## SIX - Índices da tabela

ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|D2_FILIAL+D2_COD+D2_LOCAL+D2_NUMSEQ|Produto + Armazem + Num.Sequenc.|SB1||S|
2|D2_FILIAL+D2_TP+D2_COD|Tipo Produto + Produto|XXX+SB1||S|
3|D2_FILIAL+D2_DOC+D2_SERIE+D2_CLIENTE+D2_LOJA+D2_COD+D2_ITEM|Num. Docto. + Serie + Cliente + Loja + Produto + Item|XXX+XXX+SA1+XXX+SB1||S|
4|D2_FILIAL+D2_NUMSEQ|Num.Sequenc.|||S|
5|D2_FILIAL+DTOS(D2_EMISSAO)+D2_NUMSEQ|Emissao + Num.Sequenc.|||S|
6|D2_FILIAL+D2_COD+D2_LOCAL+DTOS(D2_EMISSAO)+D2_NUMSEQ|Produto + Armazem + Emissao + Num.Sequenc.|SB1||S|
7|D2_FILIAL+D2_PDV+D2_SERIE+D2_DOC+D2_CLIENTE+D2_LOJA|Número PDV + Serie + Num. Docto. + Cliente + Loja|XXX+XXX+XXX+SA1||S|
8|D2_FILIAL+D2_PEDIDO+D2_ITEMPV|No do Pedido + Item do Ped.|XXX+XXX+XXX||S|
9|D2_FILIAL+D2_CLIENTE+D2_LOJA+D2_SERIREM+D2_REMITO+D2_ITEMREM|Cliente + Loja + Serie remito + Remito + Item remito|||S|
A|D2_FILIAL+D2_NFORI+D2_SERIORI|N.F.Original + Serie Orig.|||S|
B|D2_FILIAL+D2_ORDSEP|Ordem Sep.||ACDSD201|S|
C|D2_FILIAL+DTOS(D2_EMISSAO)+D2_ESPECIE|Emissao + Especie|||S|
D|D2_FILIAL+D2_DOC+D2_SDOC+D2_CLIENTE+D2_LOJA+D2_COD+D2_ITEM|Num. Docto. + Série Doc. + Cliente + Loja + Produto + Item|XXX+XXX+SA1+XXX+SB1||N|
E|D2_FILIAL+D2_PDV+D2_SDOC+D2_DOC+D2_CLIENTE+D2_LOJA|Número PDV + Série Doc. + Num. Docto. + Cliente + Loja|XXX+XXX+XXX+SA1||N|
F|D2_FILIAL+D2_CLIENTE+D2_LOJA+D2_SDOCREM+D2_REMITO+D2_ITEMREM|Cliente + Loja + Série Doc. + Remito + Item remito|||N|
G|D2_FILIAL+D2_NFORI+D2_SDOCORI|N.F.Original + Série Orig.|||N|
H|D2_FILIAL+D2_SERIREM+D2_REMITO|Serie remito + Remito|||S|
I|D2_FILIAL+D2_IDTRIB|Id. Tributos|||S|
J|D2_FILIAL+D2_CONTA|C Contabil|||S|
K|D2_FILIAL+D2_CTAREC|Cta Receita|||S|


