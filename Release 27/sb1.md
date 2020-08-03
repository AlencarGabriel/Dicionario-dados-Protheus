# SB1 - Descrição Genérica do Produto
## SX3 - Campos da tabela
X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|B1_AFAMAD|N|5|2|Aliq. FAMAD|Aliquota FAMAD|`@E 99.99` |`Positivo()` ||||||||
02|B1_FILIAL|C|2|0|Filial|Filial do Sistema|||||S|A|R|||
03|B1_COD|C|15|0|Codigo|Codigo do Produto|`@!` |`A093Prod(.F.).and.existchav("SB1").and.IIF(Subs(M->B1_COD,1,3)=="MOD",A010MOD(),.T.) .And. A010GRADE() .And. Freeforuse("SB1")` |||S|||||
04|B1_DESC|C|30|0|Descricao|Descricao do Produto|`@!` ||||S|||||
05|B1_CODITE|C|27|0|Cod Item|Codigo do Item|`@!` |`NaoVazio()` |||N|||||
06|B1_TIPO|C|2|0|Tipo|Tipo de Produto (MP,PA,.)|`@!` |`A010Tipo()` ||02|S|||||
07|B1_UM|C|2|0|Unidade|Unidade de Medida||`ExistCpo("SAH")` ||SAH|S|||||
08|B1_LOCPAD|C|2|0|Armazem Pad.|Armazem Padrao p/Requis.|`@!` |`ExistCpo("NNR") .and. A010VLoc()` ||NNR|N|||||
09|B1_GRUPO|C|4|0|Grupo|Grupo de Estoque|`@!` |`Vazio() .Or. (A010Grupo() .And. ExistCpo("SBM"))` ||SBM|S|||||
10|B1_PICM|N|5|2|Aliq. ICMS|Alíquota de ICMS|`@E 99.99` |`if(nModulo==11.or.nModulo==14,.t.,VldAliqIcm(M->B1_PICM))` |||N|||||
11|B1_IPI|N|5|2|Aliq. IPI|Alíquota de IPI|`@E 99.99` |`Positivo()` |||N|||||
12|B1_POSIPI|C|10|0|Pos.IPI/NCM|Nomenclatura Ext.Mercosul|`@R 9999.99.99` |`If(cModulo$"EEC/EDC/EIC/ESS",AC120Valid("B1_POSIPI"),Vazio() .Or. ExistCpo("SYD",M->B1_POSIPI))` ||SYD|S|||||
13|B1_ESPECIE|C|2|0|Especie TIPI|Especie Produto da TIPI|`@!` ||||N|||||
14|B1_EX_NCM|C|3|0|Ex-NCM|Ex-NCM - determina % I.I.|`@!` |`Empty(M->B1_POSIPI) .OR. ExistCpo("SYD",LEFT(M->B1_POSIPI,8)+"  "+M->B1_EX_NCM) .OR. Vazio()` ||WD2||||||
15|B1_EX_NBM|C|3|0|Ex-NBM|Ex-NBM - determina % IPI|`@!` |`Empty(M->B1_POSIPI) .OR. ExistCpo("SYD",LEFT(M->B1_POSIPI,8)+"  "+M->B1_EX_NBM)` ||WD3||||||
16|B1_ALIQISS|N|5|2|Aliq. ISS|Aliquota de ISS|`99.99` |`Positivo()` |||N|||||
17|B1_CODISS|C|9|0|Cod.Serv.ISS|Código de Serviço do ISS|`@9` |||60|N|||||
18|B1_TE|C|3|0|TE Padrao|Codigo de Entrada padrao|`@9` |`vazio().or.existcpo("SF4").And.M->B1_TE<="500"` ||SF4|N|||||
19|B1_TS|C|3|0|TS Padrao|Codigo de Saida padrao|`@9` |`vazio().or.existcpo("SF4").And.M->B1_TS>"500"` ||SF4|N|||||
20|B1_PICMRET|N|6|2|Solid. Saida|% Lucro Calc. Solid.Saida|`@E 999.99` |`Positivo()` |||N|||||
21|B1_PICMENT|N|6|2|Solid. Entr.|% Lucro Calc. Solid.Entr.|`@E 999.99` |`Positivo()` |||N|||||
22|B1_IMPZFRC|C|1|0|Imp.Z.Franca|Produto Import. Z.Franca|`@!` |`Pertence(' SN')` |||N|||S=Sim;N=Nao||
23|B1_BITMAP|C|20|0|Foto|Foto do Produto|||||N|||||
24|B1_SEGUM|C|2|0|Seg.Un.Medi.|Segunda Unidade de Medida||`Vazio() .Or. ExistCpo("SAH")` ||SAH|N|||||
25|B1_CONV|N|5|2|Fator Conv.|Fator de Conversao de UM|`@E 99.99` |`Positivo()` |||N|||||
26|B1_TIPCONV|C|1|0|Tipo de Conv|Tipo de Conversao da UM|`@!` |`Pertence("MD")` |"M"||N|||M=Multiplicador;D=Divisor||
27|B1_ALTER|C|15|0|Alternativo|Codigo Alternativo|`@!` |`vazio().or.existcpo("SB1")` ||ALT|N|||||
28|B1_QE|N|9|0|Qtd.Embalag.|Qtde por Embalagem|`@E 999,999,999` |`A010Mult()` |||N|||||
29|B1_PRV1|N|12|2|Preco Venda|Preco de Venda|`@E 999,999,999.99` |`A010Preco()` |||N|||||
30|B1_EMIN|N|12|2|Ponto Pedido|Ponto de Pedido|`@E 999,999,999.99` ||||N|||||
31|B1_CUSTD|N|12|2|Custo Stand.|Custo Standard|`@E 999,999,999.99` |`Positivo()` |||N|||||
32|B1_UCALSTD|D|8|0|Ult. Calculo|Dta Ult Calc do Custo Std||||||||||
33|B1_UPRC|N|12|2|Ult. Preco|Ultimo Preco de Compra|`@E 999,999,999.99` |`Positivo()` |||N|||||
34|B1_MCUSTD|C|1|0|Moeda C.Std|Moeda do Custo Standard|`@!` |`Pertence("12345")` |"1"||N|||1=Moeda1;2=Moeda2;3=Moeda3;4=Moeda4;5=Moeda5||
35|B1_UCOM|D|8|0|Ult. Compra|Data da Ultima Compra|||||N|||||
36|B1_PESO|N|11|4|Peso Liquido|Peso Liquido p/ calc N.F.|`@E 999,999.9999` |`POSITIVO(M->B1_PESO)` |||N|||||
37|B1_ESTSEG|N|12|2|Seguranca|Estoque de Seguranca|`@E 999,999,999.99` ||||N|||||
38|B1_ESTFOR|C|3|0|Form.Est.Seg|Formula Estoque Seguranca|`@!` |`vazio().or.existcpo("SM4")` ||SM4||||||
39|B1_FORPRZ|C|3|0|Form. Prazo|Formula Calculo do Prazo|`@!` |`vazio().or.existcpo("SM4")` ||SM4|N|||||
40|B1_PE|N|5|0|Entrega|Prazo de Entrega|`@E 99999` |`Positivo()` |||N|||||
41|B1_TIPE|C|1|0|Tipo Prazo|Tipo Prazo entrega(D/M/A)|`@!` ||||N|||H=Horas;D=Dias;S=Semana;M=Mes;A=Ano||
42|B1_LE|N|12|2|Lote Econom.|Lote Economico|`@E 999,999,999.99` |`A010Mult()` |||N|||||
43|B1_LM|N|12|2|Lote Minimo|Lote Minimo|`@E 999,999,999.99` |`Positivo()` |||N|||||
44|B1_CONTA|C|20|0|Cta Contabil|Conta Contabil dn Prod.|`@!` |`vazio().or. Ctb105Cta()` ||CT1|N|||||
45|B1_TOLER|N|3|0|Tolerancia|Tolerancia|`999` |`Positivo()` |||N|||||
46|B1_CC|C|9|0|Centro Custo|Centro de Custo|`@!` |`Vazio().or.Ctb105Cc()` ||CTT|N|||||
47|B1_ITEMCC|C|9|0|Item Conta|Item de Conta|`@!` |`Vazio() .Or. Ctb105Item()` ||CTD|N|||||
48|B1_FAMILIA|C|1|0|Familia|Informa 'S' se e' familia|`!` |`pertence("SN ")` |||N|||S=Sim;N=Nao||
49|B1_QB|N|7|0|Base Estrut.|Qtde Base da Estrutura|`9999999` |`Positivo()` |||N|||||
50|B1_PROC|C|6|0|Forn. Padrao|Fornecedor Padrao|`@!` |`A010Proc()` ||SA2|N|||||
51|B1_LOJPROC|C|2|0|Loja Padrao|Loja Fornecedor Padrao|`@!` |`A010LojProc()` |||N|||||
52|B1_APROPRI|C|1|0|Apropriacao|Apropr.Direta ou Indireta|`!` ||||N|||D=Direto;I=Indireto||
53|B1_TIPODEC|C|1|0|Tipo Dec. OP|Tipo de Decimais p/ OP|`!` |`Vazio() .Or. Pertence("NAIT")` |"N"||N|||N=Normal;A=Arred.5/4;I=Incrementa;T=Trunca||
54|B1_ORIGEM|C|1|0|Origem|Origem do produto|`@!` |`Vazio() .or. ExistCpo("SX5","S0"+M->B1_ORIGEM)` ||S0|N|||||
55|B1_CLASFIS|C|2|0|Class.Fiscal|Classificacao fiscal|`@!` |`Vazio().or.Texto()` |||N|||||
56|B1_FANTASM|C|1|0|Fantasma|Informa 'S' se e' fantasm|`!` ||||N|||S=Sim;N=Nao||
57|B1_RASTRO|C|1|0|Rastro|Rastreabilidade Produto|`!` |`pertence("SLN") .And. AvalLote(M->B1_COD,,.T.)` |"N"||N|||S=SubLote;L=Lote;N=Nao utiliza||
58|B1_UREV|D|8|0|Ult. Revisao|Data da Ultima Revisao|||ddatabase||N|||||
59|B1_DATREF|D|8|0|DT Referenc.|Data Referencia do Custo|||ddatabase||N|||||
60|B1_FORAEST|C|1|0|Fora estado|S-se comprado fora estado|`!` ||||N|||S=Sim;N=Nao||
61|B1_COMIS|N|5|2|% Comissao|Percentual de Comissao|`@E 99.99` |`Positivo()` ||||||||
62|B1_MONO|C|1|0|Forn. Canal|Forn. de Dominio do Canal|`@!` |||||||S=Sim;N=Nao||
63|B1_PERINV|N|3|0|Per.Invent.|Periodicidade Inventario|`999` |`Positivo()` ||||||||
64|B1_DTREFP1|D|8|0|Dt.Ref.Prc 1|Data de Ref. do Preco 1|||||N|||||
65|B1_GRTRIB|C|6|0|Grupo Trib.|Grupo de Tributacao|`@!` |`Vazio() .Or. ExistCpo("SX5","21"+M->B1_GRTRIB)` ||21|N|||||
66|B1_MRP|C|1|0|Entra MRP|Entra no Mrp?|`@!` ||"S"|||||S=Sim;N=Nao;E=Especial||
67|B1_NOTAMIN|N|1|0|Nota Minima|Nota Minima|`9` ||||N|||||
68|B1_PRVALID|N|3|0|Prazo Valid.|Prazo de Validade|`999` |`Positivo()` |||N|||||
69|B1_NUMCOP|N|5|0|Qtde. Copias|Qtde. Copias p/ C. Barras|`99999` ||||N|||||
70|B1_CONINI|D|8|0|Cons.Inicial|Data do Consumo Inicial|||||N|||||
71|B1_CONTSOC|C|1|0|Cont.Seg.Soc|Incide Contr.Seg.Social|`@!` ||||N|||S=Sim;N=Nao||
72|B1_IRRF|C|1|0|Impos.Renda|Incide imposto renda|`@!` ||||N|||S=Sim;N=Nao||
73|B1_CODBAR|C|15|0|Cod Barras|Codigo de Barras|`@!` |`A010CodBar(M->B1_CODBAR)` |||N|||||
74|B1_CODGTIN|C|15|0|Cod. GTIN|Código GTIN p/ NF-e||`A010CodBar(M->B1_CODGTIN,.F.)` ||||A|R|||
75|B1_GRADE|C|1|0|Grade|Produto pertence grade|`@!` |`Pertence("SN")` |||N|||S=Sim;N=Nao||
76|B1_FORMLOT|C|3|0|Cod Form Lot|Cod. Formula preen. Lote|`@!` |`Vazio() .Or. ExistCpo("SM4",M->B1_FORMLOT)` ||SM4|N|||||
77|B1_FPCOD|C|10|0|Cod.Familia|Codigo da Familia|`@!` |`Vazio() .or. ExistCpo("SYC",M->B1_FPCOD)` ||SYC|N|||||
78|B1_LOCALIZ|C|1|0|Contr.Endere|Controla Enderecamento|`@!` |`Pertence("SN") .And. AvalLocali(M->B1_COD)` |"N"||N|||S=Sim;N=Nao||
79|B1_OPERPAD|C|2|0|Rt.Op Padrao|Roteiro de Oper. Padrão|`@!` |`If(!Empty(M->B1_OPERPAD),ExistCPO('SG2',M->B1_COD+M->B1_OPERPAD),.T.)` ||SG2|N|||||
80|B1_DESC_P|C|6|0|Desc. Portug|Descricao em Portugues|`999999` ||||N|||||
81|B1_CONTRAT|C|1|0|Contrato|Contrato de Parceria|`@!` |`Pertence("SNA ")` |"N"||N|A|R|S=Sim;N=Nao;A=Ambos||
82|B1_DESC_GI|C|6|0|Desc. L.I.|Descricao p/ Lic. Import.|`999999` ||||N|||||
83|B1_DESC_I|C|6|0|Desc. Ingles|Descricao em Ingles|`999999` ||||N|||||
84|B1_VLREFUS|N|15|5|Val.Ref.US$|Val.Ref.US$|`@E 999,999,999.99999` |`POSITIVO(M->B1_VLREFUS)` ||||||||
85|B1_IMPORT|C|1|0|Prod. Import|Produto Importado|`!` |`Pertence("SN ")` |"N"||N|||S=Sim;N=Nao||
86|B1_VM_I|M|36|0|Desc. Ingles|Descricao em Ingles|||E_MSMM(SB1->B1_DESC_I,36)||N||V|||
87|B1_VM_GI|M|48|0|Desc. LI|Descricao da LI|||E_MSMM(SB1->B1_DESC_GI,48)||N||V|||
88|B1_VM_P|M|36|0|Desc. Portug|Descricao em Portugues|||E_MSMM(SB1->B1_DESC_P,36)||N||V|||
89|B1_OPC|C|80|0|Opc. Default|Grupo de Opcional Padrao|`@!S40` ||||N|V||||
90|B1_ANUENTE|C|1|0|Anuente|Anuente ?|`@!` |`Pertence("12")` |"2"||N|||1=Sim;2=Nao||
91|B1_CODOBS|C|6|0|Cod. Obs.|Codigo da observacao|||||N|A||||
92|B1_OBS|M|60|0|Observacao|Observacao do Produto|||If(!inclui,MSMM(SB1->B1_CODOBS,60),"")||N|A|V|||
93|B1_SITPROD|C|2|0|Situacao|Situacao do Produto||||T2|N|A||||
94|B1_FABRIC|C|20|0|Fabricante|Fabricante|||||N|||||
95|B1_MODELO|C|15|0|Modelo|Modelo do Produto|`@!` |||||||||
96|B1_SETOR|C|2|0|Setor|Setor do Supermercado|`99` |`ExistCpo("SX5","72"+M->B1_SETOR)` ||72||A||||
97|B1_BALANCA|C|1|0|Balanca|Pesavel na Balanca|`!` |`M->B1_BALANCA $ "0123"` ||||A||0=NÒo usa;1=Preþo;2=Peso;3=Unidade||
98|B1_TECLA|C|3|0|Tecla|Tecla de Atalho  Balanca|`999` |||||A||||
99|B1_PRODPAI|C|15|0|Produto Pai|Produto Pai||||||||||
A0|B1_TIPOCQ|C|1|0|Tipo de C.Q.|Tipo de C.Q. a ser usado|`@!` |`Pertence("MQ") .And. a010LotQlt()` |"M"||N|A||M=Materiais;Q=SigaQuality||
A1|B1_SOLICIT|C|1|0|Restricao|Restricao de Solicitantes|`@!` ||"N"||N|||S=Sim;N=Nao||
A2|B1_QUADPRO|C|1|0|Classe Repos|Classe de reposicao|`@!` ||||N|V|R|1=Classe I;2=Classe II;3=Classe III;4=Classe IV||
A3|B1_AGREGCU|C|1|0|Custeio OP|Control. custeio para OP|`@!` |`Pertence("12 ")` |"2"||N|A|R|1=Permite;2=Nao permite;||
A4|B1_BASE3|C|14|0|SFamilia|SubFamilia||||||A|R|||
A5|B1_GRUPCOM|C|6|0|Gr. Compras|Grupo de Compradores|`@!` |`Vazio() .Or. ExistCpo("SAJ",M->B1_GRUPCOM)` ||SAJ|N|||||
A6|B1_DESPIMP|C|1|0|Desp.Import.|Despesa de Importaçao|`@!` |`Pertence("SN ")` |"N"||N|||S=Sim;N=Nao||
A7|B1_DESBSE3|C|60|0|Des SubFam|Descr SubFamilia||||||A|R|||
A8|B1_NUMCQPR|N|3|0|Produções CQ|Envio de Produções ao CQ|`999` |`Positivo()` |||N|||||
A9|B1_CONTCQP|N|3|0|Cont.Prod.CQ|Contador de Produções CQ|`999` |`Positivo()` |||N|||||
B0|B1_REVATU|C|3|0|Rev.Estrutur|Rev. Atual da Estrutura|`@!` ||||N|||||
B1|B1_CODEMB|C|30|0|Embalagem|Codigo embalagem|`@!` |`Existcpo('EE5',M->B1_CODEMB) .Or. Vazio()` ||EE5|N|||||
B2|B1_INSS|C|1|0|Calcula INSS|Calcula INSS|`@!` ||"N"||N|||S=Sim;N=Nao||
B3|B1_ESPECIF|C|80|0|Descr.Espec.|Descrição Específica|`@!` ||||S|||||
B4|B1_MAT_PRI|C|20|0|Materia Pri.|Material Prima|`@!` ||||S|||||
B5|B1_NALNCCA|C|7|0|NALADI NCCA|NALADI NCCA|`@R 9999.99.9` |`ExistCpo("SJ2",M->B1_NALNCCA)` ||SJ2|N|||||
B6|B1_REDINSS|N|5|2|% Red. INSS|Perc. de reducao do INSS|`@E 99.99` |`Positivo()` |||N|||||
B7|B1_REDIRRF|N|5|2|% Red. IRRF|Perc. de reducao do IRRF|`@E 99.99` |`Positivo()` |||N|||||
B8|B1_NALSH|C|8|0|NALADI SH|NALADI SH|`@R 9999.99.99` |`ExistCpo("SJ1",M->B1_NALSH)` ||SJ1|N|||||
B9|B1_ALADI|C|3|0|ALADI|ALADI|`@!` |`ExistCPO("SJC",M->B1_ALADI)` ||SJC|N|||||
C0|B1_TAB_IPI|C|2|0|IPI de Pauta|Tabela para IPI de Pauta|`@!` |`(Vazio() .Or. ExistCpo('EI6'))` ||EI6|S|||||
C1|B1_GRUDES|C|3|0|Grupo Descon|Grupo de Desconto|`@!` |`FG_Seek("VE5","SBM->BM_CODMAR+M->B1_GRUDES")` ||VE5|N|||||
C2|B1_REDPIS|N|5|2|%Red.PIS|Perc. Redução PIS|`@E 99.99` |`Positivo()` ||||||||
C3|B1_REDCOF|N|5|2|% Red.COFINS|Perc.Redução COFINS|`@E 99.99` |`Positivo()` ||||||||
C4|B1_DATASUB|D|8|0|Data Substit|Data da Substituicao|`@D` |||||||||
C5|B1_PCSLL|N|5|2|Perc. CSLL|Percentual CSLL|`@E 99.99` ||||N|||||
C6|B1_PCOFINS|N|5|2|Perc. COFINS|Percentual COFINS|`@E 99.99` ||||N|||||
C7|B1_PPIS|N|5|2|Perc. PIS|Percentual PIS|`@E 99.99` |`Positivo()` |||N|||||
C8|B1_MTBF|N|9|2|MTBF em Hr.|MTBF em horas.|`@E 999,999.99` ||||N|V||||
C9|B1_MTTR|N|9|2|MTTR em Hr.|MTTR em horas.|`@E 999,999.99` ||||N|V||||
D0|B1_FLAGSUG|C|1|0|Tip Sugestao|Tipo da Sugestao|`@!` |`Pertence("1234 ")` |"1"||N|||1=Normal;2=Cancelado;3=Novo;4=Lucrativo||
D1|B1_CLASSVE|C|1|0|Status Venda|Status Venda p/ Sugestao|`@!` |`pertence("1234 ")` |"1"||N|||1=Normal;2=Promocao;3=Descarte;4=Eliminado||
D2|B1_MIDIA|C|1|0|Calc.Midia|Calcula Imposto p/Midia?|`@!` |`Pertence("12")` |"2"||N|||1=Sim;2=Nao||
D3|B1_QTMIDIA|N|14|2|Qtde. Midia|Qtde. Midia|`@E 999,999,999.99` |`Positivo()` |||N|||||
D4|B1_VLR_IPI|N|9|2|IPI de Pauta|Vlr unit. do IPI de Pauta|`@E 999,999.99` |`Positivo()` |||N|||||
D5|B1_ENVOBR|C|1|0|Env. Obrigat|Peca c/ Envio obrigatorio|`@!` |`Pertence("01")` |"0"||N|||0=Sim;1=Nao||
D6|B1_QTDSER|C|1|0|Vld Num Seri|Vlda Num. Serie 1a/2a UM|`9` ||"1"||N|||1=1a Unidade de Medida;2=2a Unidade de Medida||
D7|B1_SERIE|C|20|0|Serie/Colec.|Serie / Colecao|`@!` |`Vazio() .Or. Texto()` ||||||||
D8|B1_FAIXAS|N|2|0|Nr.faixas CD|Numero faixas CD|`99` |`Positivo()` ||||||||
D9|B1_NROPAG|N|4|0|Nro. Paginas|Numero paginas|`9999` |`Positivo()` ||||||||
E0|B1_ISBN|C|10|0|Codigo ISBN|Codigo no ISBN|`@!` |||||||||
E1|B1_TITORIG|C|50|0|Tit.Original|Titulo Original|`@!` |||||||||
E2|B1_LINGUA|C|20|0|Lingua Orig.|Lingua Original|`@!` |`Vazio().Or.Texto()` ||||||||
E3|B1_EDICAO|C|3|0|Nro.Edicao|Numero da Edicao|`@!` |`Vazio().Or.Texto()` ||||||||
E4|B1_OBSISBN|C|40|0|Obs ISBN|Observacao ISBN|`@!` |`Vazio().Or.Texto()` ||||||||
E5|B1_CLVL|C|9|0|Classe Valor|Classe Valor Contabil|`@!` |`Vazio() .Or. Ctb105ClVl()` ||CTH|N||||`CtbInUse()` |
E6|B1_ATIVO|C|1|0|Ativo|Produto Ativo (Sim/Nao)|`@!` ||"S"||N|A||||
E7|B1_EMAX|N|12|2|Estoq Maximo|Estoque Maximo|`@E 999,999,999.99` |`Positivo()` ||||||||
E8|B1_PESBRU|N|11|4|Peso Bruto|Peso Bruto|`@E 999,999.9999` |`Positivo()` |||N|A||||
E9|B1_TIPCAR|C|6|0|Tipo Carga|Tipo da Carga|`@!` |`Vazio() .Or. ExistCpo("DB0")` ||DB0|N|||||
F0|B1_FRACPER|N|5|2|Frac Permit|Fracao Permitida|`@E 99.99` |`Positivo()` |||N|A|R|||
F1|B1_INT_ICM|N|12|2|P.ICMS Prop.|Pauta do ICMS próprio|`@e 999,999.99` |`Positivo()` |0||N|A|R|||
F2|B1_VLR_ICM|N|14|2|Icms Pauta|Valor de Icms de Pauta|`@E 99,999,999.99` |`Positivo()` ||||||||
F3|B1_VLRSELO|N|15|2|Valor Selo|Vlr.selo p/caixa cigarro|`@E 999,999,999,999.99` |`POSITIVO(M->B1_VLRSELO)` ||||||||
F4|B1_CODNOR|C|3|0|Cod. Norma|Codigo da Norma|`@!` |`Vazio() .or. ExistCpo("EEI")` ||EEI|N|||||
F5|B1_CORPRI|C|6|0|Cor Princip.|Cor Principal|`@!` |`Vazio() .Or. ExistCpo("SX5","EE"+M->B1_CORPRI)` ||EE|N|||||
F6|B1_CORSEC|C|6|0|Cor Secund.|Cor Secundaria|`@!` |`Vazio() .Or. ExistCpo("SX5","EE"+M->B1_CORSEC)` ||EE|N|||||
F7|B1_NICONE|C|15|0|Icone APS|Nome do Icone no PREACTOR|`@!` ||||N|||||
F8|B1_ATRIB1|C|6|0|Atributo 1|Atributo 1|`@!` |`A612VldAtr("1")` ||AT1|N|||||
F9|B1_ATRIB2|C|6|0|Atributo 2|Atributo 2|`@!` |`A612VldAtr("2")` ||AT2|N|||||
G0|B1_ATRIB3|C|6|0|Atributo 3|Atributo 3|`@!` |`A612VldAtr("3")` ||AT3|N|||||
G1|B1_REGSEQ|C|6|0|Regra Sequ.|Regra de Sequenciamento|`@!` |`Vazio() .Or. ExistCpo("SX5","EK"+M->B1_REGSEQ)` ||EK|N|||||
G2|B1_CPOTENC|C|1|0|Contr. Poten|Controla Potencia de Lote|`!` |`pertence(" 12") .And. If(M->B1_CPOTENC$"1",If(M->B1_RASTRO$"LS",.T.,(Help(" ",1,"NAORASTRO"),.F.)),.T.)` |"2"||N|||1=Sim;2=Nao||
G3|B1_POTENCI|N|6|2|Potencia Pad|Potencia de Lote Padrao|`@E 999.99` |`If(M->B1_RASTRO$"LS".And.M->B1_CPOTENCI$"1",Positivo(),A010Potenci())` |||N|||||
G4|B1_QTDACUM|N|9|0|Qtde. Acum.|Quantidade Acumulada|`@E 999,999,999` ||||N|||||
G5|B1_QTDINIC|N|9|0|Qtd Inic Mes|Quantidade Inicial do Mes|`@E 999,999,999` ||||N|V||||
G6|B1_REQUIS|C|1|0|Requisitado|Requisitado para:||`Pertence("0123")` ||||||0=Centro de Custo;1=Paciente;2=Farmacia;3=Ambos||
G7|B1_SELO|C|1|0|Utiliza Selo|Utiliza Selo de Controle|||||N|||1=Sim;2=Nao||
G8|B1_LOTVEN|N|12|2|Qtde Venda|Qtde. minima de venda|`@E 99,999,999.99` |`Positivo()` ||||||||
G9|B1_OK|C|4|0|OK|OK||||||||||
H0|B1_USAFEFO|C|1|0|FEFO|Utiliza FEFO|`@!` |`Pertence("12")` |"1"||N||R|1=Sim;2=Não||
H1|B1_IAT|C|1|0|Trunc ou Arr|Trunca ou Arredonda|`@!` |`Pertence("AT")` |||N|A|R|||
H2|B1_IPPT|C|1|0|Prop ou Terc|Prod. Propria ou Terceiro|`@!` |`Pertence("PT")` |||N|A|R|||
H3|B1_CNATREC|C|3|0|Cod Nat Rec|Cod Nat Receita|`@!` |`ExistCpo("CCZ",M->B1_TNATREC+M->B1_CNATREC)` ||||V||||
H4|B1_TNATREC|C|4|0|Tab. Na. Rec|Tab. Nat. Receita|`@!` |`Vazio() .Or. ExistCpo('CCZ')` ||CCZSB1||||||
H5|B1_AFASEMT|N|5|2|Alíq.FASE-MT|Alíquota FASE-MT|`@E 99.99` |`Positivo()` ||||A|R|||
H6|B1_AIMAMT|N|5|2|Alíq. IMA-MT|Alíquota IMA-MT|`@E 99.99` |`Positivo()` ||||A|R|||
H7|B1_TERUM|C|2|0|Terc Un Med|Terceira Unidade de Medid|`@!` ||||N|V||||
H8|B1_AFUNDES|N|5|2|Alq.FUNDESA|Alíquota FUNDESA|`@E 99.99` |`Positivo()` ||||A|R|||
H9|B1_AFABOV|N|5|2|Aliq. FABOV|Alíquota FABOV|`@E 99.99` |`Positivo()` ||||||||
I0|B1_CODPROC|C|6|0|Cód.Desc.Pro|Cód.Desc.Processo Prod.|`999999` ||||N|A|R|||
I1|B1_CODQAD|C|13|0|Dep Correcao|Depto resp.  manut. QNC||`FQNCCHKCC(cFilAnt,M->B1_CODQAD)` ||QAD|N|A|R|||
I2|B1_COEFDCR|N|5|2|Coef. DCR|Coeficiente DCR|`@E 99.99` ||||N|A|R|||
I3|B1_CLASSE|C|6|0|Classe Selo|Classe Selo de Controle||`A010B1Class()` ||A9|N|||||
I4|B1_CHASSI|C|25|0|Num Chassi|Número Chassi Veículo|`@!` ||||N|A|R|||
I5|B1_CCCUSTO|C|9|0|CC p/ Custo|Centro de Custo Custeio.|`@!` |`Vazio() .Or. Ctb105CC()` ||CTT|N|A|R|||
I6|B1_CEST|C|9|0|CEST|Cod. Especificador ST|`@R 99.999.99` ||||N|A|R|||
I7|B1_INTEG|C|1|0|Integracao|Proveniente de Integracao|`@!` ||||N|V||1=Sim; 2 =Não||
I8|B1_GRPTIDC|C|50|0|Desc. Gr. TI|Descricao do Grupo - TI|`@!` ||IIF(!INCLUI,POSICIONE("SX5",1,XFILIAL("SX5")+"XJ"+SB1->B1_GRPTI,"X5_DESCRI"),"")||N|V|V|||
I9|B1_HREXPO|C|8|0|Hr. Ult. Exp|Hora da Ultima Exportação|||||N|V|R|||
J0|B1_GCCUSTO|C|8|0|Gr Cnt Custo|Grupo Contabil custeio.|`@!` |`Vazio() .Or. ExistCpo('CTR',,1)` ||CTR|N|A|R|||
J1|B1_GDODIF|C|1|0|Grau Dificul|Grau Dificultade||`IF ( !EMPTY(M->B1_GDODIF),EXISTCPO("SX5","GG"+M->B1_GDODIF,1),.T.)` ||GG|N|A|R|||
J2|B1_GRPCST|C|3|0|Enq. IPI|Cod. Enquadramento do IPI|`@!` |`Vazio() .or. ExistCpo("F08")` ||F08|N|A|R|||
J3|B1_GRPNATR|C|2|0|Grp.Nat.Rec.|Grupo Natureza Receita|`@!` ||||N|V|R|||
J4|B1_FUSTF|C|1|0|Fust/Funttel|Incide Fust/Funttel|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
J5|B1_FECP|N|5|2|Aliq FECP|Alíquota do FECP|`@E 99.99` ||||N|A|R|||
J6|B1_CRICMS|C|1|0|ICMS 271|Calcula Cred.ICMS-Art.271|`@!` |`Pertence(" 01")` |'0'||N|A|R|0=Nao;1=Sim||
J7|B1_DCI|C|1|0|Prod. DCI|Prod DCI Mensal|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
J8|B1_DCR|C|9|0|Nr. DCR|Numero do DCR|`@!` |`Dcigat('DCR')` |||N|A|R|||
J9|B1_DCRE|C|10|0|Nr. DCRE|Numero do DCRE|`@!` |`Dcigat('DCRE')` |||N|A|R|||
K0|B1_DCRII|N|16|7|Vl. DCRII|Valor do DCRII|`@E 99,999,999.9999999` ||||N|A|R|||
K1|B1_DIFCNAE|C|11|0|Dif. CNAE|Cod. Dif. CNAE|`@!` ||||N|A|R|||
K2|B1_DTCORTE|D|8|0|Mud.Reg.Trib|Dt. Mud Regime Tributação||||||||||
K3|B1_DTFIMNT|D|8|0|Dt.Fim N. R.|Data Fim Nat. Receita|||||N|V|R|||
K4|B1_ESCRIPI|C|1|0|Est Cred IPI|Estorno de Credito de IPI|`@!` |`Pertence(" 123")` |"3"||N|||1=M.P;2=P.A;3=Nao||
K5|B1_TIPOBN|C|2|0|Tipo BN|Tipo de Beneficiamento|`@!` |`Vazio() .Or. A010tipo()` ||02|N|||||
K6|B1_USERLGA|C|17|0|Log de Alter|Log de Alteração|||||N|V|R|||
K7|B1_USERLGI|C|17|0|Log de Inclu|Log de Inclusão|||||N|V|R|||
K8|B1_UVLRC|N|12|2|Ult Vlr Comp|Ultimo valor de compra.|`@E 999,999,999.99` ||||N|V|R|||
K9|B1_VALEPRE|C|1|0|Vale Present|Produto é Vale Presente?||`Pertence('12')` |||N|||1=Sim;2=Nao||
L0|B1_VEREAN|C|2|0|Código EAN|Código EAN|`@!` ||||N|||||
L1|B1_VIGENC|D|8|0|Data Vigenc|Data Vigencia Inicial|||||N|||||
L2|B1_VLCIF|N|12|3|Valor CIF|Valor CIF do Insumo|`@E 99,999,999.999` ||||N|A|R|||
L3|B1_UMOEC|N|2|0|Ult Moe Comp|Ultima moeda de compra.|||||N|V|R|||
L4|B1_TPPROD|C|2|0|Tipo Medic.|Tipo de Medicamento||`Vazio() .Or. ExistCpo('SX5','92'+M->B1_TPPROD)` ||92|N|A|R|||
L5|B1_TPREG|C|1|0|Tp. Reg|Tipo de Regime|`@!` |`Pertence(" 12")` |||N|||1=Não Cumulativo;2=Cumulativo||
L6|B1_TALLA|C|6|0|Tamanho|Tamanho|||||N|A|R|||
L7|B1_PRODSBP|C|1|0|Atende Nec?|Atende a Necessidade?|`@!` |`Pertence('PC')` |'C'||N|A|R|P=Produzindo;C=Comprando||
L8|B1_QBP|N|7|0|Base Pre-Es.|Qtde Base Pre-Estrutura|`9999999` |`Positivo()` |||N|A|R|||
L9|B1_REFBAS|C|1|0|Ref. Base|Referencia Base ST||`Pertence(" 012")` |||N|||0=Preço Tabelado/Maximo;1=Valor Agregado;2=Lista Negativa;3=Lista Positiva;4=Lista Neutra||
M0|B1_MARKUP|N|5|2|% Markup|Percentual de Markup|`@E 99.99` |`Positivo()` |||N|A|R|||
M1|B1_LOTESBP|N|12|2|Lote SBP|Lote Prod. Subproduto|`@E 999,999,999.99` |`Positivo()` |||N|A|R|||
M2|B1_MSBLQL|C|1|0|Blq. de Tela|Bloqueio de Tela||`pertence("12")` |"2"||N|||1=Sim;2=Não||
M3|B1_MOPC|M|80|0|M. Opcional|Mesmo opcional|`@!` |||||V|R|||
M4|B1_PARCEI|C|6|0|Parceiro|Parceiro de Venda|`@!` |`Vazio().OR.ExistCpo('AC4')` ||AC4||A|R|||
M5|B1_PIS|C|1|0|Retem PIS|Efetua a retenção-PIS|`@!` |`Pertence("12")` |"2"|||||1=Sim;2=Não||
M6|B1_PMACNUT|N|6|2|% Macronutr.|Perc. de Macronutrientes|`@E 999.99` |`Positivo()` |||N|A|R|||
M7|B1_PMICNUT|N|6|2|% Micronutr.|Perc. de Micronutrientes|`@E 999.99` |`Positivo()` |||N|A|R|||
M8|B1_VLR_PIS|N|12|2|Pis Pauta|Valor do PIS de pauta|`@e 999,999.99` |`Positivo()` |||||R|||
M9|B1_VM_PROC|M|48|0|Desc.Process|Desc.Processo Produtivo|||Iif(Inclui,"",E_MSMM(SB1->B1_CODPROC,48))||N|A|V|||
N0|B1_VLR_COF|N|12|2|COFINS Pauta|Valor do COFINS de pauta|`@e 999,999.99` |`Positivo()` |||||R|||
N1|B1_PORCPRL|C|2|0|Porc. PRL|Porcentagem PRL|`!@` |`Vazio() .Or. Pertence("20/30/40")` ||||A|R|20=20%;30=30%;40=40%||
N2|B1_PRODREC|C|1|0|Material Rec|Material Reciclavel|`@!` |`Pertence(" 12")` ||||||1=Sim;2=Nao||
N3|B1_PR43080|N|6|2|%Red.43080|%Red.Dec.43080|`@E 999.99` ||||N|||||
N4|B1_PRDORI|C|15|0|Cod. Orig.|Código Original|`@!` |`Vazio() .Or. ExistCpo("SB1")` ||SB1|N|A|R|||
N5|B1_PRFDSUL|N|12|8|Pr.Fundersul|Percentual Fundersul|`@E 999.9999999` ||||N|A|R|||
N6|B1_PRINCMG|N|6|2|Pr.Inc.Leite|Perc.Incentivo Prod.Leite|`@E 999.99` ||||N|A|R|||
N7|B1_PRN944I|C|1|0|Prod. RN944i|Produto ICMS ST A. 944I|`@!` |`Pertence("SN")` |"S"|||||S=Sim;N=Não||
N8|B1_PAUTFET|N|9|4|Pauta FETHAB|Pauta do Imposto FETHAB|`@E 9,999.9999` |||||||||
N9|B1_PERGART|N|5|2|% Garantia|Percentual da garantia|`@E 99.99` |`Positivo()` |||N|A|R|||
O0|B1_PAFMD5|C|32|0|MD5|Chave MD5 do Registro||||||||||
O1|B1_MSEXP|C|8|0|Ident.Export|Ident.Export.Dados|||||N|V|R|||
O2|B1_MEPLES|C|1|0|Exe. Serviço|Execução do Serviço|`@9 9` |`Pertence(" 12")` |||N|A|R|1=EP;2=LES||
O3|B1_IVAAJU|C|1|0|Cal. IVA Aju|Calcula IVA Ajustado|`@!` |`Pertence(" 12")` |||N|A|R|1=SIM;2=NAO||
O4|B1_REGESIM|C|1|0|Rg. Simp. MT|Rg. Simplificado MT|`@!` |`Pertence(" 12")` |||N|||1=Sim;2=Não||
O5|B1_REGRISS|C|2|0|Regra ISS Pg|Regra de ISS Progressivo|`@!` ||||N|A|R|||
O6|B1_SITTRIB|C|1|0|Sit Trib|Situação Tributária|`@!` ||||N|A|R|||
O7|B1_RETOPER|C|1|0|Ret.Operação|Retém PIS/COFINS operação|`@!` |`Pertence("12")` |"2"||N|A|R|1=Sim;2=Não||
O8|B1_SELOEN|C|6|0|Enq. Selo|Classe Enq. IPI|`@!` |||||||||
O9|B1_RICM65|C|1|0|Art65 RICMPR|Art 65 do RICMS/PR"|`@!` |`Pertence(" 12")` |"2"|||||1=Sim;2=Nao||
P0|B1_RPRODEP|C|1|0|Rel. Prodepe|Gera Relatorio Prodepe|`@!` |`Pertence(" 12")` ||||||1=Sim;2=Nao||
P1|B1_RSATIVO|C|1|0|Rastro Ativo|Rastro Ativo - IPI|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
P2|B1_TRIBMUN|C|20|0|C. Trib. Mun|Codigo de Trib. Municipal|`@!` ||||N|A|R|||
P3|B1_TIPVEC|C|6|0|Tipo Vetor|Tipo Vetor||`if (!empty(m->b1_tipvec),existcpo("SX5","VC"+M->B1_TIPVEC,1),.T.)` ||VC|N|A|R|||
P4|B1_TPDP|C|1|0|Calc. TPDP|Calcula TPDP|`@!` |`Pertence(" 12")` |||N|||1=Sim;2=Não||
P5|B1_TFETHAB|C|1|0|Tipo FETHAB|Tipo FETHAB|`@!` |`Pertence(" 12345")` |||N|A|R|1=Soja;2=Algodão;3=Gado;4=Madeira;5=Milho||
P6|B1_ESTRORI|C|15|0|Estr. Origem|"Estrutura Origem"|`@!` |`A010EstOri()` ||SG1SBP|N|A|R|||
P7|B1_DESBSE2|C|60|0|Des SubFam|Desc SubFamilia|||||N|A|R|||
P8|B1_CRICMST|C|1|0|Cont ICMS-ST|Cont Restituição ICMS-ST|`@!` |`Pertence(" 01")` |||N|A|R|0=Não;1=Sim||
P9|B1_CSLL|C|1|0|Retem CSLL|Efetua a Retenção-CSLL|`@!` |`Pertence("12")` |"2"|||||1=Sim;2=Não||
Q0|B1_CRDEST|N|5|2|Crd Estímulo|Crédito Estímulo|`@E 99.99` |`Positivo()` |||N|||||
Q1|B1_CRDPRES|N|5|2|%Cred. Pres|% Crédito Presumido|`@E 99.99` |`Positivo()` |||N|A|R|||
Q2|B1_FECPBA|N|5|2|Aliq FECP BA|Aliquota FECP Bahia|`@E 99.99` |||||||||
Q3|B1_FETHAB|C|1|0|Inc.FETHAB|Incidencia de FETHAB|`@!` |`Pertence("NS")` |"N"||N|A|R|N=Nao;S=Sim||
Q4|B1_FECOP|C|1|0|Calc. FECOP|Calcula FECOP|`@!` |`Pertence(" 12")` |||N|||1=Sim;2=Não||
Q5|B1_GARANT|C|1|0|Garantia?|Produto contém garantia?||`Pertence("12")` |"2"||N|A|R|1=Sim;2=Não|`M->B1_TIPO <> SuperGetMV("MV_LJTPGAR", ,"GE")` |
Q6|B1_FRETISS|C|1|0|F.Ret.ISS|Forme retenção ISSQN|`@!` |`Pertence(' 12')` |||N|A|R|1=Cons Vlr Minimo;2=Sempre Retem||
Q7|B1_GRPTI|C|4|0|Grupo - TI|Grupo da TES Inteligente|`@!` |`Vazio() .Or. ExistCpo("SX5","XJ"+M->B1_GRPTI)` ||XJ|N|A|R|||
Q8|B1_IDHIST|C|20|0|ID.Hist.|ID.Hist.|`@!` ||Iif(FindFunction("IdHistFis"), IdHistFis(),"")||N||R|||
Q9|B1_IMPNCM|N|14|2|Aliq. de Imp|Aliq. de Impostos|`@E 99,999,999,999.99` ||||N|A|R|||
R0|B1_CFEM|C|1|0|Cal. CFEM|Compõe Cal. CFEM|`@!` |`Pertence(" 12")` |||N|||1=Sim;2=Não||
R1|B1_CFEMA|N|6|2|Aliq. CFEMA|CFEM - Alíquota|`@E 999.99` ||||||R|||
R2|B1_CFEMS|C|1|0|Sit. CFEM|CFEM - Receita ou Deduz|`@!` |`Pertence(" 123")` |||N|||1=Receita;2=Deduz Seg.;3=Deduz Trans.||
R3|B1_CALCFET|C|1|0|Calc. FETHAB|Calcula o Imposto FETHAB|`@!` |`Pertence("12")` ||||||1=Sim;2=Não||
R4|B1_CARGAE|C|1|0|Carga Esp?|Carga Especial?|`@!` |`Pertence("12")` |"2"||||R|1=Sim;2=Não||
R5|B1_CNAE|C|9|0|CNAE|Cod. Atividade Produto|`@!` |||||A|R|||
R6|B1_CODANT|C|15|0|Cód. ant.|Código anterior|`@!` |`Vazio() .Or. ExistCpo("SB1")` ||SB1|N|A|R|||
R7|B1_COFINS|C|1|0|Retem COF|Efetua a retenção-COFINS|`@!` |`Pertence("12")` |"2"|||||1=Sim;2=Não||
R8|B1_COLOR|C|10|0|Cor|Cor|||||N|A|R|||
R9|B1_CODLAN|C|6|0|Cod.Cat83|Código Cat83|`@!` |`Vazio() .Or. ExistCpo('CDZ')` ||CDZ|N|A|R|||
S0|B1_AFACS|N|5|2|Aliq. FACS|Alíquota FACS|`@E 99.99` |`Positivo()` |||N|||||
S1|B1_AFETHAB|N|5|2|Aliq. FETHAB|Alíquota FETHAB|`@E 99.99` |`Positivo()` |||N|||||
S2|B1_ADMIN|C|10|0|Admin.|Administradora|`@!` |||PGA|N|A|R||`M->B1_TIPO == SuperGetMV("MV_LJTPGAR", ,"GE")` |
S3|B1_AJUDIF|C|1|0|Ajust/Difer|Ajuste / Diferimento|`@!` |`Pertence(" 1/2")` |||N||R|1=Sim;2=Não||
S4|B1_ALFECOP|N|5|2|Aliq. FECOP|Aliquota FECOP|`@E 99.99` |||||||||
S5|B1_ALFECRN|N|5|2|Ali.FECOP-RN|Aliquota FECOP-RN|`@E 99.99` ||||N|A|R|||
S6|B1_ALFECST|N|5|2|Al. FECOP ST|Aliquota FECOP ST|`@E 99.99` |||||||||
S7|B1_ALFUMAC|N|5|2|Alq. FUMACOP|Alíquota FUMACOP|`@E 99.99` |||||A|R|||
S8|B1_BASE|C|14|0|Cod Familia|Codigo do Familia||`if (!empty(m->b1_BASE),existcpo("SBP",+M->B1_BASE,1),.T.)` ||SBP|N|A|R|||
S9|B1_BASE2|C|14|0|SubSubFamil|SubSubfamilia|||||N|A|R|||


## SIX - Índices da tabela
ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|B1_FILIAL+B1_COD|Codigo|||S|
2|B1_FILIAL+B1_TIPO+B1_COD|Tipo + Codigo|02||S|
3|B1_FILIAL+B1_DESC+B1_COD|Descricao + Codigo|||S|
4|B1_FILIAL+B1_GRUPO+B1_COD|Grupo + Codigo|SBM||S|
5|B1_FILIAL+B1_CODBAR|Cod Barras|||S|
6|B1_FILIAL+B1_PROC|Forn. Padrao|SA2||S|
7|B1_FILIAL+B1_GRUPO+B1_CODITE|Grupo + Cod Item|||S|
8|B1_FILIAL+B1_CCCUSTO+B1_GCCUSTO|CC p/ Custo + Gr Cnt Custo|||S|
9|B1_FILIAL+B1_BASE2|SubSubFamil|||S|
A|B1_FILIAL+B1_BASE3|SFamilia|||N|
B|B1_FILIAL+B1_IDHIST|ID.Hist.|||S|
C|B1_FILIAL+B1_CONTA|Cta Contabil|||N|
D|B1_FILIAL+B1_CC|B1_|||N|


