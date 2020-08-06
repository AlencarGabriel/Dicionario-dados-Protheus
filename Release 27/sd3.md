# SD3 - Movimentações Internas
## SX3 - Campos da tabela

X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|D3_FILIAL|C|2|0|Filial|Filial do Sistema|||||N|||||
02|D3_TM|C|3|0|TP Movimento|Tipo de movimento|`@9` |`ExistCpo("SF5") .And. MaAvalPerm(2,{M->D3_TM}) .And. Iif(l250,A250TM(),A240TM())` ||SF5|S|||||
03|D3_COD|C|15|0|Produto|Codigo do Produto|`@!` |`A093Prod().And.A241PrdGrd().And. A241VLDFan(M->D3_COD)` ||SB1|S|||||
04|D3_UM|C|2|0|Unidade|Unidade de Medida||`ExistCpo("SAH")` ||SAH|S|V||||
05|D3_QUANT|N|12|2|Quantidade|Quantidade do Movimento|`@E 99999999.99` |`A240Quant()` |||S|||||
06|D3_CF|C|3|0|Tipo RE/DE|Tipo de Requisicao/devolu|`@!` ||||S|||||
07|D3_CONTA|C|20|0|C Contabil|Codigo da Conta Contabil|`@!` |`vazio().or. Ctb105Cta()` ||CT1|N|||||
08|D3_OP|C|14|0|Ord Producao|Ordem de Producao|`@9` |`vazio() .Or. A250IniOP()` ||SC2|N|||||
09|D3_LOCAL|C|2|0|Armazem|Codigo do Armazem|`@!` |`ExistCpo("NNR") .And. A240Local()` ||NNR|N|||||
10|D3_DOC|C|9|0|Documento|Numero do Documento|`@!` |`A240Doc()` |||S|||||
11|D3_EMISSAO|D|8|0|DT Emissao|Data de Emissao|`@D` |`A240Data()` |ddatabase||N|||||
12|D3_GRUPO|C|4|0|Grupo|Grupo do Produto|`@!` |||SBM|N|||||
13|D3_CUSTO1|N|14|2|Custo|Custo|`@E 999,999,999.99` |`A240Custo()` |||N|||||
14|D3_CUSTO2|N|14|2|Custo moeda2|Custo na moeda 2|`@E 999,999,999.99` |`A240Custo()` |||N|||||
15|D3_CUSTO3|N|14|2|Custo moeda3|Custo na moeda 3|`@E 999,999,999.99` |`A240Custo()` |||N|||||
16|D3_CUSTO4|N|14|2|Custo moeda4|Custo na moeda 4|`@E 999,999,999.99` |`A240Custo()` |||N|||||
17|D3_CUSTO5|N|14|2|Custo moeda5|Custo na moeda 5|`@E 999,999,999.99` |`A240Custo()` |||N|||||
18|D3_CC|C|9|0|Centro Custo|Centro de custo|`@!` |`vazio().or. Ctb105CC()` ||CTT|N|||||
19|D3_PARCTOT|C|1|0|Parc/Total|Parcial ou total|`@!` |`AParcTot("A250")` |||N|||P=Parcial;T=Total||
20|D3_ESTORNO|C|1|0|Estornado|Foi estornado (S/N) ?|`@!` |`Pertence("SN")` |||N|||S=Sim;N=Nao||
21|D3_NUMSEQ|C|6|0|Sequencial|Numeracao sequencial|`@!` ||||N|||||
22|D3_SEGUM|C|2|0|Segunda UM|Segunda Unidade de Medida||`ExistCpo("SAH")` ||SAH|N|V||||
23|D3_QTSEGUM|N|12|2|Qtd. 2a UM|Qtde na Segunda Unidade|`@E 999999999.99` |`AQtdGrade().And.A240PriUm()` |||N|||||
24|D3_TIPO|C|2|0|Tipo|Tipo do material|`@!` |||02|N|||||
25|D3_NIVEL|C|3|0|Nivel estrut|Nivel invertido estrutura|`@9` ||||N|||||
26|D3_USUARIO|C|25|0|Usuario|Usuario resp. p/digitacao|||||N|||||
27|D3_REGWMS|C|1|0|Regra WMS|Regra de Apanhe do WMS|`9` |`Pertence(" 1234")` |||S|||1=Lote;2=Numero de Serie;3=Data/Seq.Abastecimento;4=Data||
28|D3_DESCRI|C|30|0|Descr. Prod|Descrição do Produto|`@!` ||A250descbr()||N|V|V|||
29|D3_PERDA|N|11|2|Perda|Perda do Movimento|`@E 99999999.99` |`Positivo() .And. IIF(M->D3_QUANT = 0,NaoVazio(),DigiPerda(M->D3_COD,M->D3_OP,M->D3_PERDA)) .And. AQtdPerda("A250")` |||S|||||
30|D3_DTLANC|D|8|0|DT Lanc.CTB.|Data do Lancto. Contabil|||||N|||||
31|D3_TRT|C|3|0|Sequencia|Sequencia da Estrutura|`@!` ||||N|||||
32|D3_CHAVE|C|2|0|Chave|Chave de Indexação|`@!` ||||N|||||
33|D3_IDENT|C|6|0|Iden. OP Pai|Identificador da OP Pai|`@!` ||||N|||||
34|D3_SEQCALC|C|14|0|Seq.Recalc.|Seq.Recalc.Custo Médio|`@!` ||||N|||||
35|D3_RATEIO|N|6|2|% Rateio|% Rateio de Custo|`@E 999.99` |`M->D3_RATEIO > 0` |||N|||||
36|D3_LOTECTL|C|10|0|Lote|Lote||`A240Lote()` |||N|||||
37|D3_NUMLOTE|C|6|0|Sub-Lote|Sub-Lote|`@!` |`A240Lote()` |||N|||||
38|D3_DTVALID|D|8|0|Valid. Lote|Validade do Lote inform.||`A240DtVali()` |||N|||||
39|D3_LOCALIZ|C|15|0|Endereco|Endereco|`@!` |`A240Locali()` ||SBE|N|||||
40|D3_NUMSERI|C|20|0|Num de Serie|Num de Serie do Produto|`@!` |`A240NumSer()` |||N|||||
41|D3_CUSFF1|N|14|2|Custo FIFO 1|Custo FIFO Moeda 1|`@E 999,999,999.99` ||||N|||||
42|D3_CUSFF2|N|14|2|Custo FIFO 2|Custo FIFO Moeda 2|`@E 999,999,999.99` ||||N|||||
43|D3_CUSFF3|N|14|2|Custo FIFO 3|Custo FIFO Moeda 3|`@E 999,999,999.99` ||||N|||||
44|D3_CUSFF4|N|14|2|Custo FIFO 4|Custo FIFO Moeda 4|`@E 999,999,999.99` ||||N|||||
45|D3_CUSFF5|N|14|2|Custo FIFO 5|Custo FIFO Moeda 5|`@E 999,999,999.99` ||||N|||||
46|D3_ITEM|C|2|0|Item Remito|Item do Remito|`99` ||||N|||||
47|D3_OK|C|2|0|Ok|Ctrl. Interno MarkBrowse|`@!` ||||N|||||
48|D3_ITEMCTA|C|9|0|Item Contab|Item Contabil|`@!` |`vazio().or. Ctb105Item()` ||CTD|N|||||
49|D3_CLVL|C|9|0|Classe Valor|Classe Valor Contabil|`@!` |`vazio().or.Ctb105ClVl()` ||CTH|N||||`CtbInUse()` |
50|D3_PROJPMS|C|10|0|Cod.Projeto|Codigo do Projeto||`Vazio().Or.(ExistCpo("AF8") .And. PMSVldTrPr() .And. PmsVldFase("AF8",M->D3_PROJPMS,"81",.T.,,If(l240,M->D3_EMISSAO,dA241Data)))` |PmsCpoInic("D3_PROJPMS")|AF8|N|||||
51|D3_TASKPMS|C|12|0|Cod.Tarefa|Codigo da Tarefa|`@!` |`PmsVldTar('SD3') .AND. PMSVldTrPr() .AND. (Vazio().Or.A240VldPrj())` |PmsCpoInic("D3_TASKPMS")|AF9|N||||`PmsSetF3("AF9",3)` |
52|D3_ORDEM|C|6|0|Ordem Servic|Ordem de Servico|`@!` |`EXISTCPO("STJ",M->D3_ORDEM)` |||S|||||
53|D3_CODGRP|C|4|0|Grupo|Grupo Veiculos/Oficina|`@!!!!` |`VldAuxCod1("D3_CODGRP","D3_CODITE")` |IniAuxCod(SD3->D3_COD,"D3_CODGRP")|SBM|S||V|||
54|D3_CODITE|C|27|0|Cod. Produto|Produto Veiculos/Oficina|`@!` |`VldAuxCod2("D3_COD","D3_CODGRP")` |IniAuxCod(SD3->D3_COD,"D3_CODITE")|B00|S||V|||
55|D3_SERVIC|C|3|0|Cod.Servico|Codigo do Servico|`@!` |`Vazio() .Or. ExistCpo('DC5')` ||DC5|S|||||
56|D3_STSERV|C|1|0|Status Serv.|Status do Servico|`@!` |`Pertence('123')` |'1'||N|V||1=Servico Nao Executado;2=Servico Interrompido;3=Servico Executado||
57|D3_OSTEC|C|8|0|OS Ass.Tecn.|OS Assistencia Tecnica|`@!` ||||N|V||||
58|D3_POTENCI|N|6|2|Potencia Lot|Potencia do Lote|`@E 999.99` |`A240Potenc()` |||N|||||
59|D3_TPESTR|C|6|0|Estr.Fisica|Cod. da Estrutura Fisica|`@!` |`ExistCpo("DC8")` ||DC8|S|||||
60|D3_REGATEN|C|10|0|Reg.Atendim.|Registro de Atendimento||||||||||
61|D3_ITEMSWN|C|4|0|Item do SWN|Item do SWN|||||N|V||||
62|D3_DOCSWN|C|15|0|Doc SWN|Documento de SWN|||||N|V||||
63|D3_ITEMGRD|C|3|0|Item Grade|Item Grade|`@!` ||||N|V|R|||
64|D3_STATUS|C|2|0|D3_STATUS|Status de Controle Intern|||||N|||||
65|D3_CUSRP1|N|14|2|C Reposicao|Custo de Reposicao|`@E 999,999,999.99` ||||N|||||
66|D3_CUSRP2|N|14|2|C Repos.2a M|Custo de Reposicao 2a M|`@E 999,999,999.99` ||||N|||||
67|D3_CUSRP3|N|14|2|C Repos.3a M|Custo de Reposicao 3a M|`@E 999,999,999.99` ||||N|||||
68|D3_CUSRP4|N|14|2|C Repos.4a M|Custo de Reposicao 4a M|`@E 999,999,999.99` ||||N|||||
69|D3_CUSRP5|N|14|2|C Repos.5a M|Custo de Reposicao 5a M|`@E 999,999,999.99` ||||N|||||
70|D3_CMRP|N|14|4|Rep.Uni.|Custo Rep. Unitario|`@E 999,999,999.9999` ||||N|||||
71|D3_MOEDRP|C|1|0|Moeda C.Rep.|Moeda do Custo Reposicao|`@!` ||||N|||||
72|D3_REVISAO|C|3|0|Rev.Estrutur|Revisão da Estrutura|`@!` |`A201Mov(M->D3_COD,M->D3_REVISAO)` ||||A|R|||
73|D3_TANQUE|C|6|0|Tanque|Tanque|`@!` |`EXISTCPO("DH6",M->D3_TANQUE)` |||N|A|R|||
74|D3_MASSA|N|8|3|Massa Esp.|Massa Especifica do Prod.|`@E 9,999.999` ||||S|A|R|||
75|D3_TEMPAMO|N|5|2|Temp.Amostra|Temperatura da Amostra|`@E 99.99` ||||S|A|R|||
76|D3_TEMPTAQ|N|5|2|Temp.Tanque|Temperatura do Tanque|`@E 99.99` ||||S|A|R|||
77|D3_DENSAMB|N|6|4|Dens.Ambient|Densidade a Ambiente|`@E 9.9999` ||||S|A|R|||
78|D3_QTDAMB|N|9|0|Qtd.Ambiente|Quantidade Ambiente|`@E 999,999,999` ||||S|A|R|||
79|D3_FATCORR|N|6|4|Fator Correc|Fator de Correcao|`@E 9.9999` ||||S|A|R|||
80|D3_TPMOVAJ|C|2|0|Tip.Mov.Ajus|Tipo Mov. p/ ajuste|`@!` ||||S|V|R|||
81|D3_CODFOR|C|6|0|Fornecedor|Cod do Fornecedor|`@!` |`ExistCpo("SA2",M->D3_CODFOR,1)` ||SA2|N|A|R|||
82|D3_NFORP|C|6|0|Nr.Orp|Nr.Orp|`@!` |`ExistChav("SD3",M->D3_NFORP+"PR"+" ",12)` |||S|A|R|||
83|D3_LOJAFOR|C|2|0|Loja|Codigo da Loja Fornecedor|`@!` ||||N|A|R|||
84|D3_OBS|C|20|0|Obs.|Observacao|`@!` ||||N|A|R|||
85|D3_CHAVEF2|C|52|0|Chave SF2|Chave NF SF2|`@!` ||||N|V|R|||
86|D3_HAWB|C|20|0|Proc. Import|Processo de importação|`@!` ||||N|V|R|||
87|D3_IDDCF|C|6|0|Id DCF|Identificador DCF|`@!` ||||N|A|R|||
88|D3_FORNDOC|C|6|0|Fornec Doc|Fornecedor Doc|`@!` ||||N|V|R|||
89|D3_GARANTI|C|1|0|Tem Garantia|Insumo tem Garantia|`@!` |`Pertence("SN") .And. Iif(FindFunction("NGGARANSD3"),NGGARANSD3(),.T.)` |"N"||N|A|R|S=Sim;N=Não||
90|D3_LOJADOC|C|2|0|Loj Doc|Loja Documento|`@!` ||||S|V|R|||
91|D3_MOEDA|C|1|0|Moeda C.Fixo|Moeda do Custo Fixo|`@!` ||||N|||||
92|D3_NODIA|C|10|0|Seq. Diário|Seq. Diário Contabilidade|`@!` |||||||||
93|D3_NRABATE|C|8|0|N Desconto|Número Form. Desconto|`@!` ||||N|V|R|||
94|D3_NRBPIMS|C|10|0|Nr. Boletim|Numero do boletim|`@!` ||||N|V|R|||
95|D3_PERBLK|C|6|0|Per. Bloco K|Periodo Bloco K||||||||||
96|D3_NUMSA|C|6|0|Nr.S.A.|Numero da Solic.ao Armaz.|`@!` ||||N|||||
97|D3_VLRVI|N|14|2|Valor VI|Valor da Parcela Importad|`@E 99,999,999,999.99` ||||N|A||||
98|D3_QTGANHO|N|12|2|Qtde. Ganho|Qtde ganho de produção|`@E 999,999,999.99` ||||N|V|R|||
99|D3_QTMAIOR|N|12|2|Qtde. Maior|Qtde produzida a maior|`@E 999,999,999.99` ||||N|V|R|||
A0|D3_PERIMP|N|8|4|Per. Imp.|Percentual Importacao FCI|`@E 999.9999` |`If(FindFunction("A250VlPImp"),A250VlPImp(),)` |||N|A||||
A1|D3_PMACNUT|N|6|2|% Macronutr.|Perc. de Macronutrientes|`@E 999.99` |`Positivo()` |||N|A|R|||
A2|D3_PMICNUT|N|6|2|% Micronutr.|Perc. de Micronutrientes|`@E 999.99` |`Positivo()` |||N|A|R|||
A3|D3_CMFIXO|N|14|4|Cst.Fixo|Custo Unitario Fixo|`@E 999,999,999.9999` |`Positivo()` |||N|||||
A4|D3_DIACTB|C|2|0|Cód Diário|Cód Diário Contabilidade|`@!` |`ExistCPO("CVL")` ||CVL||||||
A5|D3_EMPOP|C|1|0|Empenho OP|Empenho para OP|`@!` ||||N|A|R|||
A6|D3_CHAVEF1|C|52|0|Chave NF|Chave de relac. NF|`@!` ||||N|V|R|||
A7|D3_FATHER|C|1|0|Origem|Produto Origem|||||N|A|R|||
A8|D3_CODLAN|C|6|0|Cod.Cat83|Codigo Lançamento Cat83|`@!` |`Vazio() .Or. ExistCpo('CDZ')` ||CDZ|S|A|R|||
A9|D3_CODSAF|C|15|0|Cod. Safra|Código Safra|`@!` |`Vazio() .Or. ExistCpo('NJU')` ||NJU|N|A|R|||
B0|D3_VLRPD|N|14|2|Valor PD|Valor Parcela Dedutivel|`@E 99,999,999,999.99` |||||||||
B1|D3_TEATF|C|3|0|Tipo Entrada|Tipo de Entrada da Nota|`@9` |`Vazio() .Or. ExistCpo('SF4')` ||SF4|N|A|R|||
B2|D3_OKISS|C|2|0|Marca|Marca|`@!` ||||S|A|R|||
B3|D3_OBSERVA|C|30|0|Observação|Observação|||||N|A|R|||
B4|D3_ITEMSA|C|2|0|Item S.A.|Item da Solict.ao Armaz.|`@!` |||||||||


## SIX - Índices da tabela

ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|D3_FILIAL+D3_OP+D3_COD+D3_LOCAL|Ord Producao + Produto + Armazem|SC2+SB1||S|
2|D3_FILIAL+D3_DOC+D3_COD|Documento + Produto|XXX+SB1||S|
3|D3_FILIAL+D3_COD+D3_LOCAL+D3_NUMSEQ+D3_CF|Produto + Armazem + Sequencial + Tipo RE/DE|SB1||S|
4|D3_FILIAL+D3_NUMSEQ+D3_CHAVE+D3_COD|Sequencial + Chave + Produto|XXX+XXX+SB1||S|
5|D3_FILIAL+D3_TM+D3_COD|TP Movimento + Produto|SF5+SB1||S|
6|D3_FILIAL+DTOS(D3_EMISSAO)+D3_NUMSEQ+D3_CHAVE+D3_COD|DT Emissao + Sequencial + Chave + Produto|XXX+XXX+XXX+SB1||S|
7|D3_FILIAL+D3_COD+D3_LOCAL+DTOS(D3_EMISSAO)+D3_NUMSEQ|Produto + Armazem + DT Emissao + Sequencial|SB1||S|
8|D3_FILIAL+D3_DOC+D3_NUMSEQ|Documento + Sequencial|||S|
9|D3_FILIAL+D3_DOC+D3_ITEM+D3_CF|Documento + Item Remito + Tipo RE/DE|||S|
A|D3_FILIAL+D3_PROJPMS+D3_TASKPMS+D3_COD+D3_LOCAL|Cod.Projeto + Cod.Tarefa + Produto + Armazem|||S|
B|D3_FILIAL+D3_ORDEM|Ordem Servic|||S|
C|D3_FILIAL+D3_NODIA|Seq. Diário|||S|
D|D3_FILIAL+D3_CHAVEF1|Chave NF|||N|
E|D3_FILIAL+D3_COD+D3_IDENT|Produto + Iden. OP Pai|||N|
G|D3_FILIAL+D3_CHAVEF2|Chave SF2|||S|
H|D3_FILIAL+D3_NFORP+D3_TPMOVAJ+D3_ESTORNO+DTOS(D3_EMISSAO)+D3_COD+D3_LOCAL+D3_TANQUE|Nr.Orp + Tip.Mov.Ajus + Estornado + DT Emissao + Produto + Armazem + T|||S|
I|D3_FILIAL+D3_CODFOR+D3_LOJAFOR|Fornecedor + Loja|||S|


