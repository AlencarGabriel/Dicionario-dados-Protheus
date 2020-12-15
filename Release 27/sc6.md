# SC6 - Itens dos Pedidos de Venda
## SX3 - Campos da tabela

X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|C6_FILIAL|C|2|0|Filial|Filial do Sistema|||||S|||||
02|C6_ITEM|C|2|0|Item|Numero do Item no Pedido|`@!` ||||S|V||||
03|C6_PRODUTO|C|15|0|Produto|Codigo do Produto|`@!` |`Vazio().Or.(A093Prod().And.a410Produto().And.A410MultT())` ||SB1|S|||||
04|C6_UM|C|2|0|Unidade|Unidade de Medida Primar.||`ExistCpo("SAH")` ||SAH|S|V||||
05|C6_QTDVEN|N|9|2|Quantidade|Quantidade Vendida|`@E 999999.99` |`A410QTDGRA() .AND. A410SegUm().and.A410MultT().and.a410Refr("C6_QTDVEN")` |||S|||||
06|C6_PRCVEN|N|11|2|Prc Unitario|Preco Unitario Liquido|`@E 99,999,999.99` |`A410QtdGra() .And. A410MultT() .And. A410Zera() .And. MTA410TROP(n)` |||S|||||
07|C6_VALOR|N|12|2|Vlr.Total|Valor Total do Item|`@E 999,999,999.99` |`A410MultT()` |||S|||||
08|C6_QTDLIB|N|9|2|Qtd.Liberada|Quantidade Liberada|`@E 999999.99` |`A410QTDGRA() .AND. A440Qtdl() .and. a410MultT().and.a410Refr("C6_QTDLIB")` |||N|||||
09|C6_QTDLIB2|N|9|2|Qtd.Lib 2aUM|Quantidade Liberada 2a UM|`@E 999999.99` ||||N|||||
10|C6_SEGUM|C|2|0|Segunda UM|Segunda Unidade de Medida||`ExistCpo("SAH")` ||SAH|N|V||||
11|C6_SLDALIB|N|12|2|Sld a Liber.|Saldo a Liberar|`@e 999999999.99` ||Ma440SaLib()||N|V|V|||
12|C6_OPER|C|2|0|Tp. Operacao|Tipo de Operacao||`Vazio() .Or. ExistCpo("SX5","DJ"+M->C6_OPER) .And. A410SitTrib() .And. MTA410OPER(n)` ||DJ|N||R|||
13|C6_TES|C|3|0|Tipo Saida|Tipo de Saida do Item|`@9` |`A410MultT() .And. A410SitTrib()` ||SF4|N|||||
14|C6_UNSVEN|N|9|2|Qtd Ven 2 UM|Quant. Vend. na 2 Unid M.|`@E 999999.99` |`A410Quant().and.(positivo().or.vazio())` |||N|||||
15|C6_LOCAL|C|2|0|Armazem|Armazem|`@!` |`ExistCpo("NNR") .And. A410Local()` ||NNR|N|||||
16|C6_CF|C|5|0|Cod. Fiscal|Codigo Fiscal da Operacao|`@9` |`NaoVazio().and.AvalCFO("SC6",M->C6_CF).And.MaFisGet("IT_CF")` ||13|N|||||
17|C6_QTDENT|N|9|2|Qtd.Entregue|Quantidade Entregue|`@E 999999.99` ||||N|||||
18|C6_QTDENT2|N|9|2|Qtd.Seg Ent.|Qtd.Seg. UM Entregue|`@E 999999.99` ||||N|||||
19|C6_CLI|C|6|0|Cliente|Codigo do Cliente|`@!` |`existcpo("SA1")` ||SA1|N|||||
20|C6_DESCONT|N|5|2|% Desconto|Percentual de Desconto|`@E 99.99` |`(positivo().or.vazio()).And.A410MultT()` |||N|||||
21|C6_VALDESC|N|14|2|Vlr Desconto|Valor do Desconto do Item|`@E 99,999,999,999.99` |`(Positivo().Or.Vazio()).And.A410MultT()` |||N|||||
22|C6_ENTREG|D|8|0|Entrega|Data da Entrega||`A410MultT()` |dDataBase||N|||||
23|C6_LA|C|8|0|Controles|Campo de Controle|||||N|||||
24|C6_LOJA|C|2|0|Loja|Loja do Cliente|`@!` ||||N|||||
25|C6_NOTA|C|9|0|Nota Fiscal|Numero da Nota Fiscal|`@!` ||||N|||||
26|C6_SERIE|C|3|0|Serie NF|Serie da Nota Fiscal|`!!!` ||||N|||||
27|C6_DATFAT|D|8|0|DT Ult.Fat.|Data do Faturamento|||ddatabase||N|||||
28|C6_NUM|C|6|0|Num. Pedido|Numero do Pedido|`@X` ||||N|||||
29|C6_COMIS1|N|5|2|Comissao 1|Percentual Comissao 1|`@E 99.99` |`positivo() .or. vazio()` |||N|||||
30|C6_COMIS2|N|5|2|Comissao 2|Percentual Comissao 2|`@E 99.99` |`positivo() .or. vazio()` |||N|||||
31|C6_COMIS3|N|5|2|Comissao 3|Percentual Comissao 3|`@E 99.99` |`positivo() .or. vazio()` |||N|||||
32|C6_COMIS4|N|5|2|Comissao 4|Percentual Comissao 4|`@E 99.99` |`positivo() .or. vazio()` |||N|||||
33|C6_COMIS5|N|5|2|Comissao 5|Percentual Comissao 5|`@E 99.99` |`positivo() .or. vazio()` |||N|||||
34|C6_PEDCLI|C|9|0|Ped Cliente|Numero do Pedido Cliente|`@X` ||||N||||`!"TMK"$M->C6_PEDCLI` |
35|C6_DESCRI|C|30|0|Descricao|Descricao Auxiliar|`@X` ||||N|||||
36|C6_PRUNIT|N|11|2|Prc Lista|Preco Unitario de Tabela|`@E 99,999,999.99` |`A410MultT()` |||N|||||
37|C6_BLOQUEI|C|2|0|Bloqueio|Bloqueio do Pedido|`@!` ||||N|V||||
38|C6_RESERVA|C|6|0|Num.Reserva|Numero da reserva|`@!` |`vazio().or.A410Reserv()` ||SC0|N|||||
39|C6_OP|C|2|0|OP Gerada|Flag de geracao de OP|`@!` ||||N|||||
40|C6_OK|C|2|0|Ok|Ok para Emissao de O.P.|||||N|||||
41|C6_NFORI|C|9|0|N.F.Original|N.F.Original|`@!` |`A410NfOrig()` |||N|||||
42|C6_SERIORI|C|3|0|Serie Orig.|Serie da N.F. Original|`!!!` |`A410NfOrig()` |||N|||||
43|C6_ITEMORI|C|4|0|Item NF.Orig|Nr.Item da N.Fiscal Orig.|`@!` |`A410NfOrig()` |||N|||||
44|C6_IPIDEV|N|14|2|Vl. IPI Dev.|Vl.IPI qdo.nota devolucao|`@E 999,999,999.99` |`a410DevIPI().And.MaFisGet("IT_VALIPI")` |||N|||||
45|C6_IDENTB6|C|6|0|Ident.Poder3|Identificador Poder Terc.|`@!` ||||N|V||||
46|C6_BLQ|C|2|0|Status Blq|Status do Bloqueio Pedido|`@!` |`A410QtdGra() .And. ExistCpo("SX5","F1"+M->C6_BLQ) .AND. A410MULTT()` ||F1|N|||||
47|C6_PICMRET|N|5|2|Icm Retido|Icm Retido (Margem Lucro)|`@E 99.99` |`MaFisGet("IT_MARGEM")` |||N|||||
48|C6_CODISS|C|9|0|Cod.Serv.ISS|Código de Serviço do ISS|`@9` |||60||||||
49|C6_GRADE|C|1|0|Grade|Ind.se prod.digitado Grad|`@!` |`Pertence("SN ")` |||N|V||S=Sim;N=Nao||
50|C6_ITEMGRD|C|3|0|Item Grade|Item de Grade|`@!` ||||N|V||||
51|C6_LOTECTL|C|10|0|Lote|Lote||`A410LotCTL()` |||N|||||
52|C6_NUMLOTE|C|6|0|Sub-Lote|Sub-Lote|`@!` |`A440Lote() .and. A410Zera() .And. A410LotCTL()` ||||||||
53|C6_DTVALID|D|8|0|Valid. Lote|Validade do Lote Inform.|||Ctod("")||N|V||||
54|C6_NUMORC|C|8|0|N.Orçamento|Numero do Orçamento|`@!` |`ExistCpo("SCK")` |||N|||||
55|C6_CHASSI|C|25|0|Chassi|Codigo do Chassi|`@!` ||||S|||||
56|C6_OPC|C|80|0|Opcional PV|Opcionais utilizados p/PV|`@!S40` ||||N|V||||
57|C6_LOCALIZ|C|15|0|Endereco|Endereco|`@!` |`VldLocaliz( "A440" )` ||SBE|N|||||
58|C6_NUMSERI|C|20|0|Num de Serie|Num de Serie do Produto|`@!` ||||N|||||
59|C6_NUMOP|C|6|0|Numero OP|Num. da OP gerada por PV|`@X` ||||N|V||||
60|C6_ITEMOP|C|2|0|Item da OP|Item da OP gerada por PV|`@!` ||||N|V||||
61|C6_CLASFIS|C|3|0|Sit.Tribut.|Situacao Tributaria|`@!` |`MAFISGET("IT_CLASFIS")` |||S|||||
62|C6_QTDRESE|N|12|2|Qtd.Reserva|Quant. Reservada|`@r 999,999,999.99` ||||N|V|||`.F.` |
63|C6_CONTRAT|C|6|0|No.Contrato|Nr. do Contrato Parceria|`@!` |`.F.` |||N|V|R||`.F.` |
64|C6_NUMOS|C|14|0|Nr.OS|Nr. da Ordem de Servico|`@!` |||||||||
65|C6_NUMOSFA|C|14|0|Nr.OS.Fabric|Nr.OS do Fabricante|`@!` |||||||||
66|C6_CODFAB|C|6|0|Fabricante|Codigo do Fabricante|`@!` |`a410VldFab()` ||SA1|N|||||
67|C6_LOJAFA|C|2|0|Loja Fabric.|Loja do Fabricante|`@!` |`a410VldFab()` |||N|||||
68|C6_ITEMCON|C|2|0|Item Contr.|Item de Contr. Parcerias|`@!` ||||N|V||||
69|C6_TPOP|C|1|0|Tipo Op|Tipo da Ordem de Produção|`@!` |`Pertence("FP")` |"F"||N|||F=Firme;P=Prevista||
70|C6_REVISAO|C|3|0|Revisao Estr|Revisao da Estrutura|`@!` ||||N|||||
71|C6_SERVIC|C|3|0|Servico|Tipo de Servico|`@!` |`Vazio() .Or. ExistCpo('DC5')` ||DC5|N|||||
72|C6_ENDPAD|C|15|0|End. Destino|Endereço Destino|`@!` |`Vazio() .Or. ExistCpo('SBE', M->C6_ENDPAD, 9)` ||SBE|N|||||
73|C6_TPESTR|C|6|0|Estr.Fisica|Cod. da Estrutura Fisica|`@!` |`Vazio() .Or. ExistCpo("DC8")` ||DC8|S|||||
74|C6_CONTRT|C|15|0|Contrato|Contrato de Servico|`@!` ||||N|V||||
75|C6_TPCONTR|C|1|0|Tipo Contrat|Item/Contrato de Servico|`@!` |`pertence("123")` |||N|V||1=Servicos;2=WMS;3=Manutenção||
76|C6_ITCONTR|C|2|0|It. Contrato|Item/Contrato de Servico|`@!` |`.F.` |||N|V|||`.F.` |
77|C6_GEROUPV|C|1|0|Gerou previs|Se gerou previsao de vend|||||N|||||
78|C6_PROJPMS|C|10|0|Cod.Projeto|Codigo do Projeto||`Vazio() .OR. (ExistCpo("AF8") .AND. PmsVldFase("AF8",M->C6_PROJPMS,"84"))` ||AF8|N|||||
79|C6_EDTPMS|C|12|0|Cod. EDT|Codigo da EDT|`@!` |`Vazio() .Or. A410VldPrj()` ||AFC|N||||`PmsSetF3("AFC",4)` |
80|C6_TASKPMS|C|12|0|Cod.Tarefa|Codigo da Tarefa|`@!` |`Vazio().Or.A410VldPrj()` ||AF9|N||||`PmsSetF3("AF9",4)` |
81|C6_TRT|C|3|0|Seq. Empenho|Sequencia do Empenho|`@!` |`PmsTrtSC6()` |||N|||||
82|C6_QTDEMP|N|9|2|Qt Empenhada|Quantidade Empenhada|`@E 999999.99` ||||N|||||
83|C6_QTDEMP2|N|9|2|Qt Seg. Emp|Qtd. Seg. UN Empenhada|`@E 999999.99` ||||N|||||
84|C6_PROJET|C|6|0|Contrato Tec|Contrato / Field Service|`@!` ||||N|V||||
85|C6_ITPROJ|C|2|0|It.Contrato|It.Contrato/Field Service|`@!` ||||N|V||||
86|C6_POTENCI|N|6|2|Potencia|Potencia de Lote|`@E 999.99` ||||N|V||||
87|C6_LICITA|C|6|0|Cod.Licitac.|Codigo da licitacao|`@!` |`Vazio().Or.ExistCpo("AH9")` ||AH9|N|||||
88|C6_REGWMS|C|1|0|Regra WMS|Regra de apanhe do WMS|`9` |`Vazio() .Or. Pertence("1234")` ||||||1=Lote;2=Nr de Serie;3=Data/Seq.Abastecimento;4=Data||
89|C6_MOPC|M|10|0|M. Opcional|Mesmo Opcional|`@!` ||||N|||||
90|C6_NUMCP|C|6|0|Comp. Fut.|Compromisso Futuro||`Vazio() .Or. ExistCpo("NO1")` ||||A|R|||
91|C6_NUMSC|C|6|0|Numero SC|Num. da SC gerada por PV|`@x` ||||N|V||||
92|C6_ITEMSC|C|4|0|Item SC|Item da SC gerada por PV|`@!` ||||N|V||||
93|C6_SUGENTR|D|8|0|Ent.Sugerida|Entrega Sugerida pelo APS|||dDataBase|||V|R||`TipoAPS(.F.,"DRUMMER")` |
94|C6_ITEMED|C|3|0|Item Medicao|Item da Medição|`@!` ||||N|V|R|||
95|C6_ABSCINS|N|14|2|Ab. INSS Sub|Abat. INSS Subcontrat.|`@E 999,999,999.99` |`MaFisGet("IT_ABSCINS")` ||||||||
96|C6_ABATISS|N|14|2|Abatim. ISS|Valor abatimento / ISS|`@E 99,999,999,999.99` |`MaFisGet("IT_ABVLISS").And.Positivo()` |||N|A|R|||
97|C6_ABATMAT|N|14|2|Abat. Mat.|Abatimento ISS material|`@E 99,999,999,999.99` |`MaFisGet("IT_ABMATISS").And.Positivo()` |||N|A|R|||
98|C6_VLIMPOR|N|14|2|Vl.Import|Valor da Importação|`@E 99,999,999,999.99` ||||S|A|R|||
99|C6_FUNRURA|N|14|2|Funrural|Valor do Funrural|`@E 99,999,999,999.99` ||||S|A|R|||
A0|C6_FETAB|N|14|2|Fetab|Valor do Fetab|`@E 99,999,999,999.99` ||||S|A|R|||
A1|C6_CODROM|C|6|0|Cod Romaneio|Codigo do Romaneio|`@!` ||||S|A|R|||
A2|C6_PROGRAM|C|10|0|Programa|Programa|||||N|A|R|||
A3|C6_TURNO|C|1|0|Turno|Manhã,Tarde e Noite||||||||||
A4|C6_PEDCOM|C|6|0|Ped.Compra|Ped.Compra Vinc.ao PV|`@!` |`WmsComCons()` ||SC7WMS|S|A|R|||
A5|C6_ITPC|C|4|0|Item PC|Item Ped.Compra Vinc.PV|`@!` ||||S|V|R|||
A6|C6_FILPED|C|2|0|Fil.Ped.Comp|Filial do Pedido de Compr|||||S|V|R|||
A7|C6_DTFIMNT|D|8|0|Dt.Fim N. R.|"Data Fim Nat. Receita|||||N|V|R|||
A8|C6_FCICOD|C|36|0|Codigo FCI|Código FCI|`@!` ||||N|A|R|||
A9|C6_FORDED|C|6|0|For. Ded|Fornecedor Dedução|`@!` ||||S|A|R|||
B0|C6_DATAEMB|D|8|0|Data Ini Emb|Data Inicio Embarque|||DDATABASE|||A|R|||
B1|C6_CODLAN|C|6|0|Cod. CAT83|Codigo CAT/83|`@!` |`Vazio() .Or. ExistCpo('CDZ')` ||||||||
B2|C6_LOJDED|C|2|0|Loj. Ded.|Loj. Ded.|`@!` ||||S|A|R|||
B3|C6_NUMPCOM|C|15|0|Num.Ped.Comp|Num.Ped.Comp.|`@!` ||||N|A|R|||
B4|C6_ORCGAR|C|6|0|Orca Gar Est|Orcamento Garantia Estend|`@!` ||||N|A|R|||
B5|C6_PENE|C|4|0|Peneira|Peneira|`@!` |`Vazio() .Or. ExistCpo('NP7',M->C6_PENE,1)` ||NP7|S|A|R|||
B6|C6_PVCOMOP|C|1|0|PV com OP|Pedido de Venda com OP|||||N|A|R|||
B7|C6_SOLCOM|C|6|0|Num. Solicit|Número da Solicitação de|`@!` |||||||||
B8|C6_CONTA|C|20|0|C Contabil|Conta Contábil|`@!` |`vazio() .or. Ctb105Cta()` ||CT1|N|A|R|||
B9|C6_ALMTERC|C|2|0|Armz Terc.|Armazem de Terceiros|`@!` |`IsAlmTerc(M->C6_ALMTERC)` |||N|||||
C0|C6_BASVEIC|N|16|2|V Tot NF Ent|Valor Total NF Entrada|`@E 9,999,999,999,999.99` ||||S|A|R|||
C1|C6_CLVL|C|9|0|Classe Valor|Classe Valor Contabil|`@!` |`Vazio() .Or. Ctb105ClVl()` ||CTH|N|A|R|||
C2|C6_DATCPL|D|8|0|Dt. Integ|Data da integracao||||||V|R|||
C3|C6_CTVAR|C|10|0|Cultivar|Cultivar|`@!` |`Vazio()  .Or. ExistCpo('NP4',M->C6_CTVAR,1)` ||NP4|S|A|R|||
C4|C6_HORCPL|C|8|0|Hr. Int|Hora Integracao|`99:99:99` |||||V|R|||
C5|C6_HORENT|C|4|0|Hora Entrega|Hora da Entrega|`@R 99:99` |`Vazio() .Or. AtVldHora(M->C6_HORENT)` |||S|||||
C6|C6_GCPIT|C|6|0|GCP Item|GCP Item||||||A|R|||
C7|C6_GCPLT|C|8|0|GCP Lote|GCP Lote||||||A|R|||
C8|C6_ITEMGAR|C|2|0|Item Gar Est|Item Garantia Estendida|||||N|A|R|||
C9|C6_ITEMPC|C|6|0|Item.Ped.Com|Item.Ped.Comp.|`@!` ||||N|A|R|||
D0|C6_INTROT|C|1|0|Int. Rot.|Integracao Roteirizador|`@!` |`Pertence("1234")` |"1"|||V|R|1=Não Integrado;2=Integrado;3=Falha de Integração;4=Integrado Parcial||
D1|C6_ITEMCTA|C|9|0|Item Conta|Item da Conta Contabil|`@!` |`Vazio() .Or. Ctb105Item()` ||CTD|N|A|R|||
D2|C6_ABATINS|N|14|2|Abatim. INSS|Valor abatimento / INSS|`@E 99,999,999,999.99` |`MaFisGet("IT_ABVLINSS").And.Positivo()` |||N|A|R|||
D3|C6_CATEG|C|2|0|Categoria|Categoria|`@!` |`Vazio()  .Or. ExistCpo('SX5','K1'+M->C6_CATEG,1)` ||K1|S|A|R|||
D4|C6_CC|C|9|0|C.Custo|Centro de Custo|`@!` |`Vazio() .Or. CTB105CC()` ||CTT|N|A|R|||
D5|C6_CCUSTO|C|9|0|C. de Custo|Centro de Custo|`@!` |||CTT|N|A|R|||
D6|C6_TNATREC|C|4|0|Tab. Nat. Re|Tab. Nat. Receita|`@!` |`Vazio() .Or. ExistCpo('CCZ')` ||CCZ|S|A|R|||
D7|C6_VDMOST|C|1|0|Tipo Peça|Tipo Peça|`@!` |`Pertence("NMS")` |||N|A|R|N=Normal;M=Mostruario;S=Saldao||
D8|C6_VDOBS|M|250|0|Obs. Peça|Observação da Peça|`@!` ||||N|A|R|||
D9|C6_PMSID|C|10|0|ID Protheus|ID Protheus||||||||||
E0|C6_SERDED|C|3|0|Ser. Ded.|Serie NF Dedução|`!!!` ||||S|A|R|||
E1|C6_RATEIO|C|1|0|Rateio|Rateio|`@!` ||'2'|||||1=Sim;2=Nao||
E2|C6_PCDED|N|5|2|% Ded.|Percentual de Dedução|`@E 99.99` ||||S|A|R|||
E3|C6_MOTDED|C|1|0|Mot Deduz|Motivo da Dedução|`@!` ||||S|A|R|1=Despesas com Materiais;2=Despesas com Sub-empreitada||
E4|C6_NFDED|C|9|0|NF. Ded.|NF. Dedução|`@!` ||||S|A|R|||
E5|C6_VLDED|N|16|2|Val Ded.|Valor da Dedução|`@E 9,999,999,999,999.99` ||||S|A|R|||
E6|C6_VLNFD|N|16|2|Val NF Ded.|Val NF Ded.|`@E 9,999,999,999,999.99` ||||S|A|R|||
E7|C6_TPDEDUZ|C|1|0|Tipo Deduz|Tipo de Dedução|`@!` ||||S|A|R|1=Percentual;2=Valor||
E8|C6_TPPROD|C|1|0|Tp. Prod.|Tipo do Produto||`Pertence("12")` |"1"||S|A|R|1=Venda; 2=Desenvolvimento||
E9|C6_TPREPAS|C|6|0|Tipo Repasse|Tipo de Repasse|`@!` |`Vazio() .OR. ExistCpo("SX5","0G"+M->C6_TPREPAS)` ||0G||A|R|||
F0|C6_NRSEQCQ|C|6|0|Nro.Seq. CQ|Nro. Sequencial do CQ|`@!` ||||N|V|R|||
F1|C6_REVPROD|C|3|0|Revisão|Revisão do produto|||||N|A|R|||
F2|C6_SDOC|C|3|0|Série Doc.|Série do Documento Fiscal|`!!!` ||||N|V|R|||
F3|C6_SDOCDED|C|3|0|Sér. Ded.|Série NF Dedução|`!!!` ||||N|V|R|||
F4|C6_SDOCORI|C|3|0|Série Orig.|Série da N.F. Original|`!!!` ||||N|V|R|||
F5|C6_SDOCSD1|C|3|0|Série Doc.|Série do Documento Fiscal|`!!!` ||||N|V|R|||
F6|C6_PEDVINC|C|6|0|Ped. Vinculo|Número Pedido Vinculado|`@X` |`Vazio() .Or. ExistCpo("SC5",M->C6_PEDVINC,1)` ||SC5VIN|N|A|R|||
F7|C6_PRODFIN|C|15|0|Prod Final|Produto Final|`@!` |`Vazio() .or. ExistCPO("SB1")` ||SB1||||||
F8|C6_INFAD|M|80|0|Inf. Ad. Pro|Inf. Adicionais do Prod|`@!` ||E_MSMM(SC6->C6_CODINF,80)||N|A|V|||
F9|C6_IPITRF|N|14|2|IPI Transf|Base do IPI para transfer|`@E 99,999,999,999.99` |||||||||
G0|C6_ITLPRE|C|3|0|Item L.Pres.|Item da Lista de Presente|`@!` ||||S||R|||
G1|C6_GRPNATR|C|2|0|Grp.Nat.Rec.|Grupo Natureza Receita|`@!` ||||N|V|R|||
G2|C6_CULTRA|C|10|0|Cultura|Cultura|`@!` |`Vazio() .Or. ExistCpo('NP3',M->C6_CULTRA,1)` ||NP3|S|A|R|||
G3|C6_D1DOC|C|15|0|Num.Doc.Ent.|Num. Doc. Entrada|`@!` ||||S||R|||
G4|C6_D1ITEM|C|4|0|Item NF.|Item Nota Fiscal|`@!` ||||||R|||
G5|C6_D1SERIE|C|3|0|Serie NF|Serie Nota Fiscal|`!!!` ||||S||R|||
G6|C6_CSTPIS|C|2|0|CST PIS|CST PIS|`@!` ||||N|A|R|||
G7|C6_CNATREC|C|3|0|Cod Nat Rece|Cod Nat Receita|`@!` |`ExistCpo("CCZ",M->C6_TNATREC+M->C6_CNATREC)` |||S|V|R|||
G8|C6_CODLPRE|C|6|0|Lista Pres.|Lista de Presentes|`@!` ||||S||R|||
G9|C6_CODINF|C|6|0|Cod. Inf.|Cod. Informacao Produto|||||N|V|R|||


## SIX - Índices da tabela

ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|C6_FILIAL+C6_NUM+C6_ITEM+C6_PRODUTO|Num. Pedido + Item + Produto|XXX+XXX+SB1||S|
2|C6_FILIAL+C6_PRODUTO+C6_NUM+C6_ITEM|Produto + Num. Pedido + Item|SB1||S|
3|C6_FILIAL+DTOS(C6_ENTREG)+C6_NUM+C6_ITEM|Entrega + Num. Pedido + Item|||S|
4|C6_FILIAL+C6_NOTA+C6_SERIE|Nota Fiscal + Serie NF|||S|
5|C6_FILIAL+C6_CLI+C6_LOJA+C6_PRODUTO+C6_NFORI+C6_SERIORI+C6_ITEMORI|Cliente + Loja + Produto + N.F.Original + Serie Orig. + Item NF.Orig|SA1+XXX+SB1||S|
6|C6_FILIAL+C6_CONTRT+C6_TPCONTR+C6_ITCONTR|Contrato + Tipo Contrat + It. Contrato|||S|
7|C6_FILIAL+C6_NUMOP+C6_ITEMOP|Numero OP + Item da OP|||S|
8|C6_FILIAL+C6_PROJPMS+C6_TASKPMS+C6_EDTPMS|Cod.Projeto + Cod.Tarefa + Cod. EDT|AF8+AF9+AFC||S|
9|C6_FILIAL+C6_NUMSC+C6_ITEMSC|Numero SC + Item SC|||N|
A|C6_FILIAL+C6_FILPED+C6_PEDCOM+C6_ITPC|Fil.Ped.Comp + Ped.Compra + Item PC|||N|
B|C6_FILIAL+C6_CLI+C6_LOJA+C6_PEDCLI|Cliente + Loja + Ped Cliente|||S|
C|C6_FILIAL+C6_NUM+C6_PRODUTO+C6_SOLCOM|Num. Pedido + Produto + Num. Solicit|||S|
D|C6_FILIAL+C6_NOTA+C6_SDOC|Nota Fiscal + Série Doc.|||N|
E|C6_FILIAL+C6_CLI+C6_LOJA+C6_PRODUTO+C6_NFORI+C6_SDOCORI+C6_ITEMORI|Cliente + Loja + Produto + N.F.Original + Série Orig. + Item NF.Orig|SA1+XXX+SB1||N|
F|C6_FILIAL+C6_PRODUTO+C6_PEDCOM+C6_ITPC|Produto + Ped.Compra + Item PC|||N|


