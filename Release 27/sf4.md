# SF4 - Tipos de Entrada e Saida
## SX3 - Campos da tabela

X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|F4_CRDICMA|C|1|0|Cr. ICM.Ant|Credita ICM Anterior|`@!` |`Pertence('12')` |If(SuperGetMV("MV_DEDICMA", .F., .F.),'1','2')||||R|||
02|F4_DEDDIF|C|1|0|Ded.Difal|Ded. DIFAL do total da NF|`@!` |`Pertence(' 12')` |'1'||S|A|R|1=Sim;2=Não||
03|F4_FCALCPR|C|1|0|Calc.Cr.Prs.|Forma Calc. Crd. Pres.|`@!` |`Pertence(' 1')` |||S|A|R|1=Cervejas e Chopes Artesanais - SC||
04|F4_FILIAL|C|2|0|Filial|Filial do Sistema|||||N|||||
05|F4_CODIGO|C|3|0|Cod. do Tipo|Codigo da Entrada ou Said|`@9` |`existchav("SF4").and.A080IniCpo()` |||S|||||
06|F4_TIPO|C|1|0|Tipo do TES|Tipo do TES|`!` |`A080Tipo()` |||S|||E=Entrada;S=Saida||
07|F4_ICM|C|1|0|Calcula ICMS|Calcula ICMS (SN)?|`!` |`pertence("SN")` |||S|||S=Sim;N=Nao||
08|F4_IPI|C|1|0|Calcula IPI|Calcula IPI (SNR)?|`!` |`pertence("SNR")` |||S|||S=Sim;N=Nao;R=Com.Nao Atac.||
09|F4_CREDICM|C|1|0|Cred. ICMS|Credita ICM?|`!` |`pertence("SN")` |||S|||S=Sim;N=Nao||
10|F4_CREDIPI|C|1|0|Credita IPI|Credita IPI?|`!` |`pertence("SN")` |||N|||S=Sim;N=Nao||
11|F4_DUPLIC|C|1|0|Gera Dupl.|S - para gerar duplicata|`!` |`pertence("SN")` |||N|||S=Sim;N=Nao||
12|F4_ESTOQUE|C|1|0|Atu.Estoque|S-sim/N-nao|`!` |`pertence("SN") .and. IIF(ALTERA,A080ALMOV(SF4->F4_CODIGO),.T.)` |||N|||S=Sim;N=Nao||
13|F4_CF|C|5|0|Cod. Fiscal|Codigo Fiscal da Operacao|`@9` |`(NaoVazio().and.A080IniCpo().and.ExistCpo("SX5","13"+M->F4_CF))` ||13|N|||||
14|F4_CFEXT|C|3|0|CFOP Estend|CFOP Estendido|`@!` ||||N|A|R|||
15|F4_TEXTO|C|20|0|Txt Padrao|Codigo do texto padrao|`@!` ||||S|||||
16|F4_BASEICM|N|5|2|%Red.do ICMS|% Reducao da Base de ICMS|`@E 99.99` |`Positivo()` |||N|||||
17|F4_BASEIPI|N|5|2|%Red.do IPI|% Reducao da Base de IPI|`@E 99.99` |`Positivo()` |||N|||||
18|F4_PODER3|C|1|0|Poder Terc.|Qdo trata poder de tercei|`!` |`pertence("RDN") .and. A080VLTE3()` |||N|||R=Remessa;D=Devolucao;N=Nao Controla||
19|F4_LFICM|C|1|0|L.Fisc. ICMS|T/I/O/Nao/Zerado/Observ|`!` |`pertence("TIONZB").and.A080IniCpo()` |||N|||T=Tributado;I=Isento;O=Outros;N=Nao;Z=ICMS Zerado;B=Observacao||
20|F4_LFIPI|C|1|0|L.Fiscal IPI|T/I/O/Nao/Zerado|`!` |`PERTENCE("TIONZP").AND.A080INICPO()` |||N|||T=Tributado;I=Isento;O=Outros;N=Nao;Z=IPI Zerado;P=Vl.IPI Outr.ICM||
21|F4_DESTACA|C|1|0|Destaca IPI|Destaca IPI na nota ?|`!` |`pertence("SN")` |||N|||S=Sim;N=Nao||
22|F4_INCIDE|C|1|0|IPI na base|Incide IPI na base ?|`!` |`pertence("SNFO")` |||N|||S=Sim;N=Nao;F=Consumidor Final;O=Vl.IPI Outr.ICM||
23|F4_COMPL|C|1|0|Calc.Dif.Icm|Calcula Dif. Icm ?|`@!` |`Pertence("SN")` |||N|||S=Sim;N=Nao||
24|F4_IPIFRET|C|1|0|Calc.Ipi.Fre|Incide IPI s/ Frete|`@!` |`pertence("SNO ")` |"S"||N|||S=Sim;N=Nao;O=Outros||
25|F4_ISS|C|1|0|Calculo ISS|Incide ISS ?|`@!` |`pertence("SN ")` |"N"||N|||S=Sim;N=Nao||
26|F4_LFISS|C|1|0|L.Fiscal ISS|T/I/O/Nao|`!` |`pertence("TION")` |"N"||N|||T=Tributado;I=Isento;O=Outros;N=Nao calcula||
27|F4_NRLIVRO|C|1|0|Nr. Livro|Numero do Livro|`@!` |`Pertence(" 1234567890")` |||S|||||
28|F4_UPRC|C|1|0|Atu.Pr.Compr|Atualiza Preco Compra|`!` |`Pertence(" SN")` |"N"||N|||S=Sim;N=Nao||
29|F4_CONSUMO|C|1|0|Mat.Consumo|Material de Consumo?|`!` |`Pertence("SNO")` |"N"||N|||S=Sim;N=Não;O=Outros||
30|F4_FORMULA|C|3|0|Formula|Fórmula p/uso L.Fiscal|`@!` |||SM4||||||
31|F4_AGREG|C|1|0|Agrega Valor|Agrega Valor a Mercadoria|`@!` |`Pertence("SNIABCDEFGHR ")` |"S"||N|||I=ICMS+Mer;A=ICMS;S=Sim;N=Nao;B=IC+Mer-EIC;C=IC-EIC;D=Ded IC V.Ct;E=Ded IC Dup;F=Ded V.Mer Dup;G=V.Dup IC;H=IC ST;R=Ded IC V.Unt||
32|F4_INCSOL|C|1|0|Agrega Solid|Agrega ICMS retido na NF.|`@!` |`Vazio() .Or. Pertence("SNADE")` |"S"||N|||S=Sim;N=Nao;A=Mercadoria;D=Deduz Retido;E=Desc. ICMS ST||
33|F4_CIAP|C|1|0|L.Fisc. CIAP|Livro Fiscal CIAP|`@!` |`Pertence("SN")` |"N"||N|||S=Sim;N=Nao||
34|F4_DESPIPI|C|1|0|Desp.Ac. IPI|Desp.Base IPI - Devolucao|`@!` |`pertence("SNO")` |"S"|||||S=Sim;N=Nao;O=Outros||
35|F4_LIVRO|C|64|0|Form. Livro|Formula para Livro Fiscal|`@!S32` |`a080Livro()` |||S|A||||
36|F4_ATUTEC|C|1|0|Atual.Tecn.|Atualiza SigaTec|`@!` |`Pertence("SN")` |"N"||N|||S=Sim;N=Nao||
37|F4_ATUATF|C|1|0|Atual.Ativo|Atualiza Ativo Fixo|`@!` |`Pertence("SN")` |"N"||N|||S=Sim;N=Nao||
38|F4_TPIPI|C|1|0|IPI Bruto|IPI Bruto / Liquido|`@!` |`Pertence("BL")` |"B"||N|||B=Bruto;L=Liquido||
39|F4_STDESC|C|1|0|Bs.ICMS ST|Base do ICMS ST|`@!` |`Pertence("12")` |"1"||N|||1=Vlr.Liquido;2=Vlr.Bruto||
40|F4_BSICMST|N|6|2|%Red.ICMS ST|% Reducao de ICMS ST|`@E 999.99` |`Positivo()` |||N|||||
41|F4_CREDST|C|1|0|Crd.ICMS ST|Credita ICMS ST ?|`@!` |`Pertence("1234")` |"2"||N|||1=Credita;2=Retido ST;3=Debita;4=Subst. Trib.||
42|F4_BASEISS|N|5|2|%Red.do ISS|% Reducao do ISS|`@E 99.99` |`Positivo()` |||N|||||
43|F4_DESPICM|C|1|0|Desp.Ac.ICMS|Desp.Base ICMS ?|`@!` |`Pertence("12345 ")` |"1"||N|||1=Sim;2=Nao;3=Somente ICMSST;4=Somente ICMS normal;5=Somente Despesas||
44|F4_SITTRIB|C|2|0|Sit.Trib.ICM|Situacao Trib. do ICMS|`@!` |`Vazio() .or. ExistCpo("SX5","S2"+M->F4_SITTRIB)` ||S2|N|||||
45|F4_PISCOF|C|1|0|PIS/COFINS|Define se gera PIS/COFINS|`!` |`pertence("1234")` |"4"|||||1=PIS;2=COFINS;3=Ambos;4=Nao Considera||
46|F4_PISCRED|C|1|0|Cred.PIS/COF|Credita PIS/COFINS|`@!` |`pertence("12345")` |"3"||N|||1=Credita;2=Debita;3=Nao Calcula;4=Calcula;5=Exclusão de Base||
47|F4_TESDV|C|3|0|Tes Devol.|Tes de Devolucao|`@!` |`Vazio() .Or.(ExistCpo("SF4") .And. MaAvalTes(IIf(M->F4_TIPO=="E","S","E"),M->F4_TESDV)) .and. A080VLTE3()` ||SF4|N|||||
48|F4_BASEPIS|N|6|2|%Base PIS|% Redução do PIS|`@e 999.99` |`Positivo()` |0||N|A|R|||
49|F4_BASECOF|N|6|2|%Base COF|% Reducäo do COFINS|`@e 999.99` |`Positivo()` |||N|A|R|||
50|F4_IPILICM|C|1|0|IPI s/N.Trib|IPI nas colunas nao Trib.|`!` |`Pertence("12")` |"2"||N|||1=Sim;2=Nao||
51|F4_MOVPRJ|C|1|0|Mov. Projet.|Movimentacao do projeto|`!` |`Pertence("12345")` |"1"||N|||1=Receita;2=Despesa;3=Não movimenta;4=Dev.Despesa;5=Receita/Despesa||
52|F4_ICMSDIF|C|1|0|ICM Diferido|Diferimento de ICMS|`@!` |`Pertence("1234567")` |"2"||N|||1=Diferido;2=Nao Diferido;3=Dif. de Redução;4=Dif. Incentivo;5=Dif. com ST;6=Deduz NF e Duplicata;7=Ded. ICMS BC. Composta||
53|F4_TESP3|C|3|0|Tes Ret.Simb|Tes de retorno p/terceiro|`@!` |`Vazio() .Or. (ExistCpo("SF4").And.MaAvalTes(M->F4_TIPO,M->F4_TESP3))` ||SF4|N|||||
54|F4_QTDZERO|C|1|0|Qtd.Zerada|Permite Quantidade Zerada|`@!` |`Pertence("12")` |"2"||N|||1=Sim;2=Nao||
55|F4_SLDNPT|C|1|0|Sld.Poder 3|Saldo Poder de Terceiro|`@!` |`Pertence("12")` |"2"||N|||1=Disponivel para faturamento;2=Indisponivel||
56|F4_DEVZERO|C|1|0|Custo Dev.|Cons. Custo na Devolucao||`Pertence("12 ")` |"1"||N|||1=Sim;2=Nao|`M->F4_TIPO=="E"` |
57|F4_MSBLQL|C|1|0|Bloqueado|Bloqueia o uso da TES|`@!` |`pertence("12")` |"2"|||||1=Sim;2=Näo||
58|F4_TIPOPER|C|1|0|Tipo Operac.|Tipo da Operacao|`@!` ||||N|||||
59|F4_TRFICM|C|1|0|Trf.Deb/Crd.|Transf. Debito ou Credito|`@!` |`Pertence("12")` |"2"||N|||1=Sim;2=Nao||
60|F4_TESENV|C|3|0|TES P/envios|TES para envios||`(ExistCpo("SF4").And.MaAvalTes(M->F4_TIPO,M->F4_TESENV))` ||SF4|N|||||
61|F4_OBSICM|C|1|0|Icms Observ.|Icms na Observacao|`@!` |`Pertence("12")` ||||||1=Sim;2=Nao||
62|F4_OBSSOL|C|1|0|Solid. Obs|Solidario na observacao|`@!` |`Pertence("12345")` ||||||1=Sim;2=Nao;3=ICMS Garantido;4=ICMS Garantido Integral;5=ICMS-ST Transportes||
63|F4_PICMDIF|N|6|2|Perc.ICM DIF|Perc.do ICMS Diferido|`@e 999.99` |`Positivo()` |100|||||||
64|F4_SELO|C|1|0|Utiliza Selo|Utiliza Selo de Controle|`!` |`Pertence("1234")` |||N|||1=Venda/Compra;2=Remessa/Devolucao;3=Outros;4=Näo Movimenta||
65|F4_ISSST|C|1|0|Pgto Imposto|Pagamento Imposto|`@!` ||||N|A|R|#Iif(FindFunction("cBoxISSST"),cBoxISSST(),"")||
66|F4_FINALID|C|254|0|Finalidade|Finalidade TES|`@!` ||||N|||||
67|F4_PISFISC|C|1|0|Aplic.Credit|Aplic. Crédito PIS/COFINS|`@!` ||||S|||1=Fiscal/Estoque;2=Estoque||
68|F4_CONTSOC|C|1|0|Cont.Seg.Soc|Incide Contr.Seg.Social|`@!` |`Pertence(' 12')` |||S|A|R|1=Sim;2=Não||
69|F4_COP|C|4|0|Clas Op. Pre|Classe de Operacao ou Pre||`Vazio() .Or. ExistCpo('SX5','VZ'+M->F4_COP)` ||VZ|S|A|R|||
70|F4_INDNTFR|C|1|0|Ind.Nat.Fret|Ind.Nat.Frete||`Pertence(" 0/1/2/3/4/5/9")` |||S|A|R|0=Op.Vend.estab.vend.;1=Op.Vend.adiq.;2=Op.Comp.ger.cred.;3=Op.Comp.nao.ger.cred.;4=Trans.prod.acab.;5=Trans.prod.elab;9=Outras||
71|F4_CODBCC|C|2|0|Cod.BC Cred.|Cod.BC Cred.||`Vazio() .Or. ExistCpo('SX5','MZ'+M->F4_CODBCC)` ||MZ|S|A|R|||
72|F4_AJUSTE|C|1|0|Ajuste CIAP|Ajuste CIAP|`@!` ||||S|||||
73|F4_CPPRODE|N|5|2|Crd.PRODEPE|Perc.Crd. Pres. PRODEPE|`@E 99.99` ||||S|A||||
74|F4_TPPRODE|C|1|0|Tipo PRODEPE|Tipo Crd.Pres PRODEPE||`pertence(" 0123456789")` |||S|A||0=N Incentivado;1=Ind-Crd.Pres;2=Ind-Fin.Parcelas;3=Ind-Crd.Pres.Inter;4=Dist-Crd.Pres Entrada;5=Dist-Crd.Pres Saida;6=Import.||
75|F4_CPRECTR|C|1|0|C.Pre.Carg|Cr.Pres. Carga Tribut|`@!` ||||S|A|R|1=Sim;2=Não||
76|F4_IPIANT|C|1|0|IPI.BC.Ant|IPI.BC.ICMS Antecipado|`@!` ||||S|A|R|1=Sim;2=Não||
77|F4_TPCPRES|C|1|0|Tp Cred Pres|Tipo de Crédito Presumido|`@!` ||||S|A|R|C=Cred.Tot.oper.;B=Cred. BC ICMS;R=Cred.BC ICMS C/R;F=Tot.Oper.Lim.Fret./Paut.;M=Cred.Val.Merc.;N=Val.ICMS.||
78|F4_DESPCOF|C|1|0|Desp.Ac.COF|Desp.Ac.COF|`@!` ||||S|||1=Sim;2=Não||
79|F4_DESPPIS|C|1|0|Desp.Ac.PIS|Desp.Ac.PIS|`@!` ||||S|||1=Sim;2=Nao||
80|F4_CRPRELE|N|5|2|% Cr Prs Ele|% Crd Pres Eletronicos|`@E 99.99` |`Positivo()` |||S|A|R|||
81|F4_CRPRST|N|5|2|Cred  Pr ST|Crd Pres ST Transp|`@E 99.99` |`Positivo()` |||N|A|R|||
82|F4_CTIPI|C|2|0|Cod.Trib.IPI|Código de Tributação IPI|`@!` |`Vazio() .Or. ExistCpo('SX5','S3'+M->F4_CTIPI)` ||S3|N|A|R|||
83|F4_CRDPRES|N|8|4|Crd. Pres.|Perc. Créd. Pres.|`@E 999.9999` |`Positivo() .And. M->F4_CRDPRES <= 100` ||||||||
84|F4_CRDEST|C|1|0|Calc. Crd. E|Cálculo Crédito Estímulo|`@!` ||"1"|||||1=Não Calcula;2=Equipamentos Eletrônicos;3=Construção Civil;4=Pelo NCM||
85|F4_COFBRUT|C|1|0|COFINS Bruto|COFINS Bruto|`@!` ||"2"||S|A|R|1=Sim;2=Näo||
86|F4_COFDSZF|C|1|0|COFINS Z.F.|COFINS Zona Franca|`@!` ||"2"||S|A|R|1=Sim;2=Näo||
87|F4_IPIPC|C|1|0|IPI na BC|IPI na Base de calculo|`@!` |`Pertence(" 12")` |||S|A|R|1=Sim;2=Não||
88|F4_MKPCMP|C|1|0|Mkp ICM.Comp|Markup ICMS complementar|`@!` |`Pertence("12")` |"2"|||A|R|1=Sim;2=Näo||
89|F4_LFICMST|C|1|0|LF ICMS-ST|Livro Fiscal ICMS-ST|`@!` ||"N"||S|A|R|N=Näo;I=Isentas;O=Outras;T=Tributadas||
90|F4_ICMSST|C|1|0|ICMS s/ST|ICMS s/ST|`@!` |`Pertence("12")` |||N|||1=Sim;2=Não||
91|F4_FRETAUT|C|1|0|Frete Aut.|Frete Autonomo|`@!` |`Pertence("123")` |"1"|||||1=ICMS Proprio;2=ICMS-ST;3=ST Autônomo||
92|F4_DSPRDIC|C|1|0|Desp.Ac.ICM|Desp.Ac.Redução de ICMS|`@!` |`Pertence("123")` |||||R|1=Aplica redução de ICMS;2=Não aplica redução de ICMS;3=Não incide na base do ICMS||
93|F4_ALICRST|N|6|2|Alq. Crd. ST|Alíquota Crédito ICMSST|`@E 999.99` ||||S|A||||
94|F4_AGRPIS|C|1|0|Agr.PIS|Agrega PIS|`@!` |`Pertence("12PD ")` |"2"||S|A|R|1=Sim;2=Não;P=PIS+Merc;D=Deduz||
95|F4_AGRRETC|C|1|0|Agr.Soli Col|Agrega Solidario Colunas|`@!` ||"2"||S|A|R|1=Sim;2=Nao||
96|F4_AFRMM|C|1|0|Calc. AFRMM|Calcula AFRMM|`@!` |||||||S=Sim;N=Nao||
97|F4_AGRCOF|C|1|0|Agr.COFINS.|Agrega COFINS|`@!` |`Pertence("12CD ")` |"2"||S|A|R|1=Sim;2=Não;C=COF+Merc;D=Deduz||
98|F4_BENSATF|C|1|0|Desme.IT.ATF|Desmembra itens no ativo|`@!` |`pertence("12")` |"2"||N||R|1=Sim;2=Nao||
99|F4_BCRDCOF|N|6|2|%B.C. COFINS|Perc. Base Credito COFINS|`@E 999.99` |`Positivo()` |||N|A|R|||
A0|F4_BCRDPIS|N|6|2|%B Cred.PIS|Perc. Base Credito PIS|`@E 999.99` |`Positivo()` |||N|A|R|||
A1|F4_TRANFIL|C|1|0|Trans filial|Transferência filiais|`@!` |`Pertence(" 12")` |"2"||N||R|1=Sim;2=Nao;||
A2|F4_TPREG|C|1|0|Tp Reg|Tipo de Regime|`@!` |||||||1=Não Cumulativo;2=Cumulativo;3=Ambos||
A3|F4_REGDSTA|C|1|0|Reg. DSTA|Gera DSTA|`@!` |||||||||
A4|F4_PISBRUT|C|1|0|PIS Bruto|PIS Bruto|`@!` ||"2"||S|A|R|1=Sim;2=Näo||
A5|F4_RETISS|C|1|0|Ret. ISS|Retem ISS|`@!` |||||A||S=Sim;N=Não||
A6|F4_OPEMOV|C|2|0|Op.Movimento|Operacao de Movimento|`@!` |`ExistCpo("SX5","VS"+M->F4_OPEMOV)` ||VS||||||
A7|F4_PISDSZF|C|1|0|PIS Z.Franca|PIS Zona Franca|`@!` ||"2"||S|A|R|1=Sim;2=Näo||
A8|F4_TRIBPRD|C|2|0|Trib. Padrão|Trib. Padrão Prefeiura|`@!` |`Vazio() .Or. ExistCpo('SX5','k4'+M->F4_TRIBPRD)` ||K4|S|A|R|||
A9|F4_OPANRE|C|7|0|Op.Nao Regul|Operac. Agente nao Regul.|`9999999` |||D3C|N|A|R|||
B0|F4_COPSIMP|C|7|0|Cod Op. SIMP|Codigo da Oper. SIMP|`9999999` |`ExistCpo("D3C",M->F4_COPSIMP,2) .Or. Vazio(M->F4_COPSIMP)` ||D3C|S|A|R|||
B1|F4_IPIPECR|N|6|2|% Crd.IPI|% Credito de IPI|`@E 999.99` |`Positivo()` |||S|A|R|||
B2|F4_TXAPIPI|C|3|0|Txt Ap.IPI|Txt Apur.IPI|`@!` |`ExistCpo('SX5','87'+M->F4_TXAPIPI)` |||S|A|R|||
B3|F4_TESE3|C|3|0|Tes Rem.Simb|Tes de remessa p/terceiro|`@!` |`Vazio() .Or. (ExistCpo("SF4") .And. MaAvalTes(IIf(M->F4_TIPO=="E","S","E"),M->F4_TESE3))` ||SF4|N|||||
B4|F4_REGESP|C|2|0|Reg Especial|Regime Especial NFERJ|`@!` ||||S|A|R|00=Nenhum;01=Microemp Munic;02=Estimativa;03=Soc Prof;04=Cooperativa;05=Microempreendedor Individual;06=Art. 33;||
B5|F4_TEMDOCS|C|1|0|Possui Docs|Possui documentos|`@!` |`Pertence("1/2")` |'2'||N|A|R|1=Sim;2=Nao|`M->F4_DUPLIC == "S"` |
B6|F4_STLIQ|C|1|0|Calc.ST Liq.|Calcula ICMS ST Líquido|`@!` |`Pertence(" 12")` |||S|A|R|1=Sim;2=Nao||
B7|F4_STREDU|C|1|0|Redução ST|Redução de Base - ICMS-ST|`@!` ||||S|A|R|1=Antes da composição da base;2=Após a composição da base||
B8|F4_TABGIAC|C|3|0|Cod.Cred.Gia|Códigos de CredPres Gia|`@!` |||||||||
B9|F4_TRAFILI|C|1|0|Trf Mat|Ind Transf Mat|`@!` |`Pertence(" 12")` |"1"||S|A|R|1=Nao;2=Sim||
C0|F4_TREGDMA|C|2|0|Tp.Reg. DMA|Tipo Registro DMA|`@ 99` |`ExistCpo("SX5","84"+M->F4_TREGDMA)` ||84|N|A|R|||
C1|F4_TIPODUB|C|1|0|Tipo DUB|Tipo Ato Legal DUB|`@!` |`Pertence(" 123456")` |||S|||1=Convênio;2=Lei;3=Decreto;4=Protocolo;5=Resolução;6=Portaria||
C2|F4_TPOP|C|2|0|Tp Operação|Tipo Operação|`@!` ||||N|||||
C3|F4_TNATREC|C|4|0|Tab. Nat. Re|Tab. Nat. Receita|`@!` |`Vazio() .OR. ExistCpo('CCZ')` ||CCZ|S|A|R|||
C4|F4_NUMDUB|C|12|0|Num./Ano DUB|Num./Ano Ato Legal DUB|`@!` ||||S|||||
C5|F4_OPERGAR|C|1|0|Garantia|Operação com Garantia?|`@!` |`Pertence(' 12')` |||N|A|R|1=Sim;2=Não||
C6|F4_OPERSUC|C|1|0|Oper.Sucata|Operacao com Sucata ?|`@!` |`Pertence(" 12")` |"2"||S|||1=Sim;2=Não||
C7|F4_OUTPERC|N|6|2|% Def.MVA/Pa|% Def. Util. MVA/Pauta|`@E 999.99` ||||S|A|R|||
C8|F4_PARTICM|C|1|0|Part ICM|Partilha de ICMS||`Pertence(" 12")` |"1"||S|A||1=Nao;2=Sim||
C9|F4_PERCATM|N|5|2|P. Carga Med|Percentual de Carga Média|`@E 99.99` ||||N|A|R|||
D0|F4_PERCMED|N|7|4|Perc. Med.|Perc.Médio de Cre. do Imp|`@E 99.9999` ||||S|A|R|||
D1|F4_RFETALG|C|1|0|Ret.Fethab|Retém FETHAB Algodão|`@!` |`Pertence(" 12")` |||S|A|R|1=Sim;2=Nao||
D2|F4_RDBSICM|C|1|0|Red.Car.ICMS|Reduz Carga Tribut. ICMS|`@!` |`Pertence(" 12")` |||S|A||1=Nao;2=Sim||
D3|F4_RECDAC|C|1|0|Tp Receitas|Tipo de Receitas|`@!` ||||S|A|R|1=Mercado Interno Tributada;2=Mercado Interno Não Tributada;3=Exportação||
D4|F4_REDANT|N|5|2|%Red. Antec.|Reducao Antecip. ICMS|`@E 99.99` ||||S|A||||
D5|F4_PISMIN|C|1|0|PIS Val.Min|Apl. PIS Val.Minimo|`@!` |`Pertence(" 12")` |"2"||S|A||1=Sim;2=Nao||
D6|F4_MOVFIS|C|1|0|Mov.Fisica|Movimentação Fisica|`@!` |`Pertence("SN")` |||N|A||S=Sim;N=Nao||
D7|F4_PSCFST|C|1|0|Pis/Cof ST|Pis/Cofins ST|`@!` ||||S|A|R|1=Sim;2=Nao;3=Aliq.Zero||
D8|F4_VARATAC|C|1|0|Est Var/Atac|Est Var/Atac|`@!` |`Pertence(" 12")` |||S|A||1=Varejista;2=Atacadista||
D9|F4_VDASOFT|C|1|0|Vda Software|Operação venda Software|`@!` |`pertence("12")` |"2"||N|A|R|1=Sim;2=Não||
E0|F4_VENPRES|C|1|0|Venda Pres.|Venda Presencial|`@!` |`'Pertence(" 12")'` |||S|A|R|||
E1|F4_IPIVFCF|C|1|0|IPI Bs.ICMS|IPI Bs.ICMS Venda Futura|`@!` |`Pertence(" 123")` |"1"||S|A||1=Nao;2=ICMS;3=ICMS/ST||
E2|F4_IPIMIN|C|1|0|IPI Val.Min|Apl. IPI Val.Minimo|`@!` |`Pertence(" 12")` |"2"||S|A||1=Sim;2=Nao||
E3|F4_IPIOBS|C|1|0|Gera IPI Obs|Gera IPI na Observação|`@!` ||"1"|||||1=Sim;2=Nao||
E4|F4_ISEFECP|C|1|0|Isen. FECP|Isencao do FECP|`@!` |`Pertence(" 12") .And. IIF(ALTERA,A080ALMOV(SF4->F4_CODIGO),.T.)` |||S|||1=Sim;2=Não||
E5|F4_IVAUTIL|N|7|4|IVA Utilizad|Indice de Valor acrescido|`@E 99.9999` ||||S|A|R|||
E6|F4_ISEFEMT|C|1|0|Is.FECP-MT|Isencao FECP-MT|`@!` |`Pertence(' 12')` |||S|A|R|1=Sim;2=Nao||
E7|F4_MALQCOF|N|6|2|Aliq. COF M.|Aliquota COFINS Majorada|`@E 999.99` ||||S|A|R|||
E8|F4_MALQPIS|N|6|2|Aliq. PIS M.|Aliquota PIS Majorada|`@E 999.99` ||||S|A|R|||
E9|F4_NATOPER|C|10|0|Natureza Ope|Natureza da Operacao|`@!` |`Vazio() .Or. ExistCpo('CD1')` ||CD1|S|A|R|||
F0|F4_NATOPNF|C|3|0|Nat.Op. NFSe|Natureza operação NFS-e|`@!` |`Vazio() .Or. ExistCpo("SX5","VX"+M->F4_NATOPNF)` ||VX|N|A|R|||
F1|F4_NORESP|C|1|0|Norma Esp.|NF. Norma Especifica|`@!` |`Pertence("12")` |"2"||N|A|R|1=Sim;2=Nao||
F2|F4_DTFIMNT|D|8|0|Dt.Fim N. R.|Data Fim Nat. Receita|||||S|A|R|||
F3|F4_DUPLIPI|C|1|0|Ger.Dup.IPI|Gera Duplicata do IPI|`@!` |`Pertence("12")` |"2"||S|A|R|1=Sim;2=Nao||
F4|F4_EFDF100|C|1|0|Gera F100?|Gera registro F100?|`@!` |`Pertence(" 123")` |||S|A|R|1=Débito;2=Crédito;3=Não||
F5|F4_EFUTUR|C|1|0|Entr. Futura|Entrega Futura|`@!` |`Pertence("012")` |"0"||S|A||0=Nao;1=Recebimento da Compra com Entrega Futura;2=Recebimento da Entrega da Compra com Ent. Futura||
F6|F4_FORINFC|C|3|0|Fórmula NFE|Fórmula NFE|`@!` |||SM4|S|A|R|||
F7|F4_ESTCRED|N|6|2|% Est Cr/Deb|Perc Estorno Cred./Deb.|`@E 999.99` ||||N|A|R|||
F8|F4_ICMSTMT|C|1|0|Ded.ICM.ST|Deduz o ICMS Prop.?|||||N|A||1=Sim;2=Não||
F9|F4_IDHIST|C|20|0|ID Hist.|ID Histórico|`@!` ||Iif(FindFunction("IdHistFis"), IdHistFis(),"")||N|V|R|||
G0|F4_IMPIND|C|1|0|Imp. Indiret|Importação Indireta|`@!` |`Pertence(' 12')` |"2"||S|A|R|1=Sim;2=Nao||
G1|F4_GRPNATR|C|2|0|Grp.Nat.Rec.|Grupo Natureza Receita|`@!` ||||S|V|R|||
G2|F4_FTATUSC|C|1|0|Frt.Ativ.Uso|Frete Ativo/Uso e consumo||`Pertence(" 12")` |||S|A|R|1=Sim;2=Não||
G3|F4_INDVF|C|1|0|Ind.V.Fut|Ind.Ved.Futura|`@!` |`Pertence(" 12")` |||S|A|R|1=Sim;2=Não||
G4|F4_COMPONE|C|1|0|Componente|Bem Componente|`@!` |`Pertence(' 12')` |||S|A|R|1=Sim;2=Não||
G5|F4_CODOBSE|C|6|0|Cod Observ|Código Observ|`@!` |`'ExistCpo("CCE")'` ||CCE|N|A|R|||
G6|F4_COFMIN|C|1|0|COF Val.Min|Apl. PIS Val.Minimo|`@!` |`Pertence(" 12")` |"2"||S|A||1=Sim;2=Nao||
G7|F4_CONSIND|C|1|0|Consig Indus|Consignação Industrial|`@!` |`Pertence(' 12')` |||S|A|R|1=Sim;2=Não||
G8|F4_CREDPRE|N|5|2|Crd. Pres.|Credito Presumido RS|`@E 99.99` ||||S|A|R|||
G9|F4_CRICMST|C|1|0|Cont ICMS-ST|Cont Restituicao ICMS-ST|`@!` |`'Pertence(" 01")'` |||S|A|R|0=Nao;1=Sim||
H0|F4_CRDTRAN|N|5|2|Crd. Transp.|Perc. Cred. Pres.Transp.|`@E 99.99` ||||S|||||
H1|F4_CREDACU|C|1|0|Cr Acum ICMS|Credito Acumulado de ICMS|`@!` ||"3"||S|||#Iif(FindFunction("cBoxCrdAcu"),cBoxCrdAcu(),"")||
H2|F4_CPRESPR|N|5|2|Cr Pres PR|Cred Pres Paraná art.631|`@E 99.99` ||||S|A||||
H3|F4_CRDACUM|C|1|0|Op Cred Acum|Operacoes de credito acum|`@!` |`Pertence(' 12')` |"1"||S|A|R|1=Sim;2=Não||
H4|F4_CSTPF1|C|2|0|CST P. F100|CST de PIS para registro|`@!` |`Vazio().Or.ExistCpo('SX5','SX'+M->F4_CSTPF1)` ||SX|S|A|R|||
H5|F4_CSOSN|C|3|0|Cod Sit SN|Cod Sit Ope SN|`@!` |`Vazio() .or. ExistCpo("SX5","SG"+M->F4_CSOSN)` ||SG|N|A|R|||
H6|F4_CSTCF1|C|2|0|CST C. F100|CST de COFINS para regist|`@!` |`Vazio() .Or. ExistCpo('SX5','SX'+M->F4_CSTCF1)` ||SX|S|A|R|||
H7|F4_CSBHISS|C|5|0|Cód Su DESBH|Cód Subitem DESBH|`@!` ||||S|A|R|||
H8|F4_CROUTSP|N|5|2|Cr Out SP|Cred. Outorgado SP|`@E 99.99` ||||N|A||||
H9|F4_CRPRSIM|N|5|2|% Cr Pre Sim|Perc Cred Pres Simples|`@E 99.99` ||||N|A|R|||
I0|F4_DESTRUI|C|1|0|Destruição|Saida Destruição|`@!` |`Pertence("12")` |"2"||S|A|R|1=Sim;2=Nao||
I1|F4_DEVPARC|C|1|0|Dev.Par.Prop|Dev. Parcial Prop|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
I2|F4_DICMFUN|C|1|0|Ded.ICMS Fun|Ded.ICMS Funr|`@!` |`Pertence(" 12")` |"2"||S|A|R|1=Sim;2=Nao||
I3|F4_CTBHISS|C|9|0|Cód Tr DESBH|Cód Tributação DESBH|`@!` ||||S|A|R|||
I4|F4_DESCOND|C|1|0|Desc Condici|Desconto Condicional|`@!` |`Pertence("12")` |"2"||N|A|R|1=Sim;2=Nao||
I5|F4_CV139|C|1|0|Conv.139|Convênio 139|`@!` |`Pertence("12 ")` |||S|A|R|1=Sim;2=Nao||
I6|F4_BENDUB|C|1|0|Benefic.DUB|Especie Beneficio DUB|`@!` |`Pertence(" 123456")` |||S|||1=Dif.Compra Ativ.Imobilizado;2=Dif.Pag.Futuro;3=Isenção;4=Red.Bs.Calculo;5=Cred.Presumido;6=Outros||
I7|F4_BSRDICM|C|1|0|Bas.Calc.Red|Acres.Desp.Base.Calc.Red.|`@!` |`Pertence(" 12")` |||N|A|R|1=Produto + Despesas;2=Produto||
I8|F4_BSRURAL|C|1|0|Bas.FUNRURAL|Acres.Desp.Base FUNRURAL|`@!` |`Pertence(" 123")` |"1"||N|A|R|1=Produto Rural;2=Produto + Despesas;3=Produto + Despesas + IPI + ST||
I9|F4_CFPS|C|6|0|Cod. CFPS|Código CFPS|`999999` ||||N|||||
J0|F4_CFABOV|C|1|0|Calc. FABOV|Calcula FABOV|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Nao||
J1|F4_CFACS|C|1|0|Calc. FACS|Calcula FACS|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Nao||
J2|F4_CFAMAD|C|1|0|Calc. Famad|Calcula Famad|`@!` |`Pertence(" 12")` |"2"||S|A||1=Sim;2=Nao||
J3|F4_CODDET|C|4|0|Cod.Detalhe|Cod.Det.Isent/N.Tr|`@!` ||||S|||||
J4|F4_BSICMRE|C|1|0|Base ST Dif|Base St Diferenciado||`Pertence (" 12")` |"2"||S|A||1=Val Aquisicao; 2= Padrao||
J5|F4_CNATREC|C|3|0|Cod Nat Rece|Cod Nat Receita|`@!` |`ExistCpo("CCZ",M->F4_TNATREC+M->F4_CNATREC)` |||S|V|R|||
J6|F4_CIAPTRB|C|1|0|Trib.CIAP|Tributa CIAP|`@!` |`Pertence(" 12")` |"2"||N|A||1=Sim;2=Não||
J7|F4_AGRDRED|C|1|0|Agreg Ded|Agreg Ded|`@!` |`Pertence("12")` |||S|A|R|1=Sim;2=Não||
J8|F4_ANTICMS|C|1|0|Antecip.ICMS|Antecipação Tribut. ICMS|`@!` |`Pertence(' 12')` |||S|A||1=Sim;2=Não||
J9|F4_APLIIVA|C|1|0|Aplica Marg.|Aplica Margem de Lucro?|`@!` |`Pertence("12345")` |"2"||N|A|R|1=Sim;2=Nao;3=Maior/Menor;4=Ating.75%;5=Out.%||
K0|F4_APLIRED|C|1|0|Red.Carg.Trb|Red.Val.Carga Trb.do.ST|`@!` |`Pertence(' 1234')` |||S|A|R|1=Sim;2=Nao;3=Prop.Aliq;4=Aliq.ST||
K1|F4_APLREDP|C|1|0|Apl.Red.Prop|Apl.Red.ICM Prop. no.ST|`@!` |`Pertence(" 12")` |"2"||N|A|R|1=Sim;2=Não||
K2|F4_APSCFST|C|1|0|AgPis/CofST|Agrega Pis/CofST|`@!` |`Pertence(" 12")` |'"1"'||S|A|R|1=Sim;2=Não||
K3|F4_AGRPEDG|C|1|0|Agr.Vl.Pedg?|Agrega Valor do Pedagio ?|`@!` |`Pertence("123")` |"3"||N|A|R|1=Agregar na base ICMS;2=Agregar somente no total NF;3=Nao considera||
K4|F4_ATACVAR|C|1|0|ST.Atac/Var|ST Atacado e Varejo Calc|`@!` |`Pertence(" 12")` |"2"||N|A|R|1=Sim;2=Não||
K5|F4_FEEF|C|1|0|Calc. FEEF?|Calcula FEEF ?|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
K6|F4_FRETISS|C|1|0|For Ret ISS|Considera MV_VRETISS|`@!` |`Pertence(" 12")` |||S|A|R|1=Cons Vlr Mín.;2=Sempre Retém||
K7|F4_ENQLEG|C|2|0|Enq.leg.|Cod. Enq. legal CAT207|`@!` |`Vazio() .Or. ExistCpo("CFE")` ||CFE2|N|A|R||`.T.` |
K8|F4_ESCRDPR|C|1|0|Crd.Pres.ES|Credito Presumido ES|`@!` |`Pertence(" 12")` |"1"||N|A|R|1=Sim;2=Não||
K9|F4_DUPLIST|C|1|0|Duplicata ST|Gera Duplicata do ICMS ST|`@!` |`Pertence("12")` |"2"||N|A|R|1=Sim;2=Não||
L0|F4_INFITEM|C|8|0|Inf. item|Inf. Adicionais do item|`@!` |`Vazio() .Or. ExistCpo('F2Y')` ||F2Y|S|A|R|||
L1|F4_INOVAUT|C|1|0|Inovar Auto|Inovar Auto|`@!` |`Pertence(' 12')` |"2"||N|A|R|1=Sim;2=Não||
L2|F4_INTBSIC|C|1|0|PS/CF Import|Pis/Cof Importação|`@!` |`Pertence(" 0123")` |"0"||S|||0=Não Calcula;1=PIS Import;2=Cofins Import;3=Ambos||
L3|F4_INDDET|C|1|0|Ind Det Oper|Ind. Det. Operação|`@!` |`pertence(" 012345679")` |||S|A|R|0=PS Transp;1=PS Comun;2=Sub Entr;3=Sub Saida; 4=Distr Forn Cont;5=Escr Ctr Aut;6=Escr Ctr Vinc;7=Inf Rev Est;9=Inf Rev Fora||
L4|F4_INDISEN|C|1|0|Ind Isen Prv|Ind Isent Contr Previdenc|`@!` |`Pertence('12')` |'2'||S|A|R|1=Sim;2=Não||
L5|F4_FTRICMS|N|8|5|Fat.Desc.ICM|Fator de Redução Desc.ICM|`@E 99.99999` ||||N|A|R|||
L6|F4_GRPCST|C|3|0|Enq. IPI|Enquadramento do IPI|`@!` |`Vazio() .or. ExistCpo("F08")` ||F08|N|A|R|||
L7|F4_MKPSOL|C|1|0|Marg.Solid.|Modo de aplicacao margem|`@!` |`Pertence("123")` ||||||1=Nunca;2=Configuracao;3=Sempre||
L8|F4_MOTICMS|C|2|0|Mot.Desone.|Mot.Desone. ICMS|`@!` ||||N|A|R|#cBoxMotICM()||
L9|F4_MSGLT|C|1|0|Imp Msg Lote|Impressão Msg. do Lote|`@!` ||||S|A|R|1=Sim;2=Não||
M0|F4_MTRTBH|C|2|0|Mt Ret DESBH|Mt Ret DESBH|`@!` |`ExistCpo("SX5","GQ"+M->F4_MTRTBH)` ||GQ|S|A|R|||
M1|F4_ISEFERN|C|1|0|Isen.FECOP|Isencao FECOP-RN|`@!` |`Pertence(' 12')` |||S|A|R|1=Sim;2=Não||
M2|F4_ISEFEMG|C|1|0|Is.FECP-MG|Isencao FECP-MG|`@!` |`Pertence(' 12')` |||S|A|R|1=SIm;2=Não||
M3|F4_IPMMG|C|60|0|Cod. IPM MG|Código IPM MG|`@!` |`vazio().or.CLN->(dbseek(xFilial("CLN")+Right(ReadVar(),2)+M->F4_IPMMG)) .And. Empty(CLN->CLN_DTFIMV)` ||CLN|S|A|R|||
M4|F4_IPMSP|C|60|0|Cod. IPM SP|Código IPM SP|`@!` |`vazio().or.CLN->(dbseek(xFilial("CLN")+Right(ReadVar(),2)+M->F4_IPMSP)) .And. Empty(CLN->CLN_DTFIMV)` ||CLN|S|A|R|||
M5|F4_DBSTCSL|C|1|0|Csll/Icm Ret|Csll/Icms Ret BC?|`@!` ||||N|A|R|1=Sim;2=Não||
M6|F4_DBSTIRR|C|1|0|Irrf/Icm Ret|Irrf/Icms Ret BC?|`@!` ||||N|A|R|1=Sim;2=Não||
M7|F4_DESCISS|C|1|0|Desc. ISS|Descontos Inc. Base ISS|`@!` |`Vazio() .Or. Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
M8|F4_DIFAL|C|1|0|Calc. Difal|Calcula Difal ICMS|`@!` |`Pertence(" 12")` |||S|A|R|1=Sim;2=Não||
M9|F4_DIFALPC|C|1|0|Ded. Dif. PC|Ded. Difal BC PIS COFINS|`@!` ||||S|A|R|1=Sim;2=Não||
N0|F4_CSENAR|C|1|0|Calc.SENAR|Calcula SENAR|`@!` |`Pertence(" 12")` |||S|A|R|1=Sim;2=Não||
N1|F4_CRPREPE|N|5|2|Crd Pres PE|Perc.Crd. Pres Pernambuco|`@E 99.99` ||||N|A|R|||
N2|F4_CRPREPR|N|5|2|Crd Pres PR|Perc. Créd. Pres. Paraná|`@E 99.99` ||||N|A|R|||
N3|F4_CRPRERO|N|5|2|Crd Pres RO|Perc. Crd. Pres. Rondônia|`@E 99.99` ||||N|A|R|||
N4|F4_CRPRESP|N|5|2|Cr Pres SP|Cred Presumido SP|`@E 99.99` ||||N|A|R|||
N5|F4_CSTCOF|C|2|0|Sit.Trib.COF|Cod.Sit.Trib. COFINS|`@!` |`Vazio() .Or. ExistCpo('SX5','SX'+M->F4_CSTCOF)` ||SX|S|A|R|||
N6|F4_CSTISS|C|2|0|Sit.Trib.ISS|Situacao Trib. do ISS|`@!` |`Vazio() .or. ExistCpo("SX5","S9"+M->F4_CSTISS)` ||S9|N|A||||
N7|F4_CSTPIS|C|2|0|Sit.Trib.PIS|Cod.Sit.Trib. PIS|`@!` |`Vazio() .Or. ExistCpo('SX5','SX'+M->F4_CSTPIS)` ||SX|S|A|R|||
N8|F4_CUSENTR|C|1|0|Custo Entr?|Valor Custo Entrada|`@!` |`Vazio() .Or. Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
N9|F4_CRLEIT|C|1|0|Art.488-MG|Trata Art.488 RICMS-MG|`@!` |`Pertence("12")` |"2"||N|A|R|1=Sim;2=Não||
O0|F4_CROUTGO|N|5|2|%Crd Out GO|Perc. Cred. Outorgado GO|`@E 99.99` ||||N|A|R|||
O1|F4_CRICMS|C|1|0|Contr.ICMS|Controle Cred.ICMSArt.271|`@!` |`Pertence(" 01")` |||S|A|R|0=Nao;1=Sim||
O2|F4_COLVDIF|C|1|0|Col ICMS Dif|Coluna ICMS Diferido|`@!` ||||S|A|R|1=Outros;2=Isento||
O3|F4_CODINFC|C|6|0|Cod.Inf.|Código da informação Comp|`@!` |||CCE|S|A|R|||
O4|F4_CODLAN|C|6|0|Cod.Cat83|Codigo Lcto Cat83|`@!` |`Vazio() .Or. ExistCpo('CDZ')` ||CDZ|S|||||
O5|F4_CODLEG|C|4|0|Cod.Legal|Cod.Enquad.Legal|`@!` |`Vazio() .Or. ExistCpo('CCV')` ||CCV1|S|||||
O6|F4_CODPAG|C|2|0|C. Pagamento|Cod. Pagamento Cat 156|`@!` |||||||01=C. Debito;02=C. Credito;03=Boleto;04=Inter. Financeira;05=Dinheiro/Cheque;06=Sedex Cobrar;99=Outros||
O7|F4_COMPRED|C|1|0|Cons.Red.Cmp|Cons. red. ICMS no comp.|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
O8|F4_CONTERC|C|1|0|Amz. Terc.?|Controla Amz. Terceiros?|`@!` |`Pertence(" 12")` ||||||1=Sim;2=Não||
O9|F4_ART274|C|1|0|Inf.ST.Ant|Inf.ST.Anterior|||||S|A|R|||
P0|F4_APLREPC|C|1|0|Apl.Red.PisC|Aplica Redução PIS/COFINS|`@!` |`pertence(" 1234")` |"4"||N|A|R|1=PIS;2=COFINS;3=Ambos;4=Nao Considera||
P1|F4_AGREGCP|C|1|0|Agreg CrdPre|Agrega Credito Presumido|`@!` |`Pertence(" 12")` |"1"||N|A|R|1=Sim;2=Não||
P2|F4_AGRISS|C|1|0|Agrega ISS|Agrega ISS|`@!` |`Pertence(" 12")` |||S|A|R|1=Sim;2=Não||
P3|F4_ALIQPRO|N|5|2|Aliq.PROT.GO|Aliquota PROTEGE-GO|`@E 99.99` ||||S|A|R|||
P4|F4_ALQFEEF|N|5|2|Aliq.FEEF.RJ|Aliquota FEEF-RJ|`@E 99.99` ||||N|A|R|||
P5|F4_ALSENAR|N|5|2|Aliq.Senar|Aliquota Senar|`@E 99.99` ||||S|A|R|||
P6|F4_CIMAMT|C|1|0|Calc. IMA-MT|Calcula IMA-MT|`@!` |`Pertence(" 12")` |||S|A|R|1=Sim; 2=Não||
P7|F4_CINSS|C|1|0|Calc.INSS|Calcula INSS|`@!` |`Pertence(" 12")` |||S|A|R|1=Sim;2=Não||
P8|F4_CLFDSUL|C|1|0|Cl.Fundersul|Calcula Fundersul?|`@!` ||||N|A|R|1=Sim;2=Não||
P9|F4_CFASE|C|1|0|Calc. FASE|Calcula FASE-MT|`@` |`Pertence(" 12")` |||S|A|R|1=Sim; 2=Não||
Q0|F4_CFUNDES|C|1|0|Calc.FUNDESA|Calcula FUNDESA|`@!` |`Pertence(" 12")` |||S|A|R|1=Sim; 2=Não||
Q1|F4_BICMCMP|C|1|0|Red.BCIC Com|Reduz ICMS Complementar|`@!` ||||S|A|R|1=Sim;2=Nao||
Q2|F4_BONIF|C|1|0|Bonificação|Entrada de bonificação ?|`@!` |`Pertence("SN ")` |" "|||A|R|S=Sim;N=Não||
Q3|F4_CALCCPB|C|1|0|Calc.CPRB|Calcula CPRB|`@!` |`Pertence(" 12")` |||S|A|R|1=Sim;2=Não||
Q4|F4_CALCFET|C|1|0|Calc. FETHAB|Calcula FETHAB|`@!` |`Pertence("12")` ||||||1=Sim;2=Não||
Q5|F4_BASCMP|N|5|2|%Red.do Difa|% Reducao da Base de Difa|`@E 99.99` |`Positivo()` |||S|A|R|||
Q6|F4_BCPCST|C|1|0|PS/CF ST BC|PS/CF ST Compoe BC ICM ST|`@!` |`Pertence(" 12")` |||S|A|R|1=Sim;2=Não||
Q7|F4_VLAGREG|C|1|0|Agr Vlr Mun|Valores agregados por Mun|`@!` |`Pertence(" SD")` |||N|A|R|S=Soma;D=Deduz||
Q8|F4_VLRZERO|C|1|0|Vlr. Zerado|Valor Zerado|`@!` |`Pertence('12')` |"2"||S|||1=Sim;2=Não||
Q9|F4_TRFICST|C|1|0|Cons.ICMS ST|Considera o ICMS ST custo|`@!` |`Pertence(' 12')` |||N|||1=Sim;2=Nao;||
R0|F4_PR35701|N|5|2|Pr.Red.PE|Pr.Red.Art.35701-PE|`@E 99.99` |`Positivo()` |||N|||||
R1|F4_PRZESP|C|1|0|Prz. Esp.|Prazo Especial|||||N|A|R|||
R2|F4_REDBCCE|N|5|2|Perc.Red.CE|Perc. de Redução-CE|`@E 99.99` ||||S|A|R|||
R3|F4_REFATAN|C|1|0|Rem. Fat.Ant|Remessa Fat.Ant ?|`@!` ||||N|A|R|1=Sim;2=Não||
R4|F4_RGESPCI|C|1|0|Reg.Esp.CIAP|Regime Especial CIAP|`@!` |`Pertence(' 12')` |||S|A|R|||
R5|F4_RGESPST|C|1|0|Reg.Esp.ST|Regime Especial ST|`@!` |`Pertence(' 12')` |||S|A|R|1=Sim;2=Não||
R6|F4_PAUTICM|C|1|0|Paut.ICMS PP|Pauta ICMS Proprio|`@!` |`Pertence(" 12")` |"1"||N|A|R|1=Sim;2=Não||
R7|F4_PCREDAC|N|6|2|%Cr Acu ICMS|Perc Cred Acumul ICMS|`@E 999.99` ||||N|A||||
R8|F4_PAGCOM|C|1|0|Pg. Comissao|Pag. Comissao|`@!` |||||||0=Nao;1=Sim||
R9|F4_TIPOTES|C|1|0|Incl./Discr|Incluido ou Discriminado|`@!` |`PERTENCE("12 ")` |"2"|||A|R|1=Incluido;2=Discriminado||
S0|F4_TRANSIT|C|1|0|Trf.transito|Transfere p/ Amz.Transito|`@!` ||||S|A|R|S=Sim;N=Nao||
S1|F4_TRANCQ|C|1|0|Trans.Fil CQ|Trans. Filial Armazem CQ|`@!` |`Pertence(' 12')` |||N|A||1=Sim;2=Nao;||
S2|F4_TPRSPL|C|1|0|TP Rec. Simp|TP Rec. Simples N|`@!` |`Pertence(" 123")` |||S|A|R|1=Comércio;2=Indústria;3=Serviços||
S3|F4_TABGIAI|C|3|0|Tab.Isen.Gia|Tabela de Isencao da GIA|`@!` ||||S|A|R|||
S4|F4_TABGIAO|C|3|0|Tab Gia Out.|Tabela Outros da GIA|`@!` ||||S|A|R|||
S5|F4_SOMAIPI|C|1|0|IPI Bs.ICMST|IPI Bas.Calc.ICMS-ST|`@!` ||"1"||S|A|R|1=Sim;2=Não||
S6|F4_STCONF|C|1|0|ST.Conf.CE|ST Confeccao CE|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Nao||
S7|F4_RESSARC|C|1|0|Ressarc.|Ressarcimento|`@!` |`Pertence('12')` |||S|A|R|1=Não;2=Sim||


## SIX - Índices da tabela

ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|F4_FILIAL+F4_CODIGO|Cod. do Tipo|||S|
2|F4_FILIAL+F4_TESENV|TES P/envios|||S|
3|F4_FILIAL+F4_IDHIST|ID Hist.|||S|
4|F4_FILIAL+F4_COPSIMP|Cod Op. SIMP|||S|


