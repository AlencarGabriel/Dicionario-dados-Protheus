# SA2 - Fornecedores
## SX3 - Campos da tabela

X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|A2_GROSSIR|C|1|0|Base Calc IR|Base de Cálculo IRRF|`@!` ||||N|A|R|0=Sem Gross UP;1=Imp. Serv. IRRF;2=Imp. Serv. IRRF + CIDE;3=Imp. Serv. IRRF + Val. Serviço||
02|A2_FILIAL|C|2|0|Filial|Filial do Sistema|||||N|||||
03|A2_COD|C|6|0|Codigo|Codigo do Fornecedor|`@!` |`IIF(Empty(M->A2_LOJA),.T.,ExistChav("SA2",M->A2_COD+M->A2_LOJA,,"EXISTFOR"))` |||S|||||
04|A2_LOJA|C|2|0|Loja|Loja do Fornecedor|`@!` |`existchav("SA2",M->a2_cod+M->a2_loja,,"EXISTFOR")` |||S|||||
05|A2_NOME|C|40|0|Razao Social|Nome ou Razao Social|`@!` ||||S|||||
06|A2_NREDUZ|C|20|0|N Fantasia|Nome de Fantasia|`@!` ||||S|||||
07|A2_END|C|40|0|Endereco|Endereco do Fornecedor|`@!` ||||S|||||
08|A2_NR_END|C|6|0|Numero|Numero do Endereco|||||N|||||
09|A2_BAIRRO|C|20|0|Bairro|Bairro do Fornecedor|`@!S15` ||||S|||||
10|A2_EST|C|2|0|Estado|Sigla da Federacao|`@!` |`ExistCpo("SX5","12"+M->A2_EST)` ||12|N|||||
11|A2_CONTPRE|C|1|0|Contrib.Prev|Contrib. Previdenciario|`@!` |`Pertence(" 12")` |"1"||S|A||1=Sim;2=Não||
12|A2_ESTADO|C|20|0|Nome Estado|Nome do Estado Fornecedor|`@!S20` ||||N|||||
13|A2_COD_MUN|C|5|0|Cod. Municip|Codigo do Municipio|`@99999` |`ExistCpo("CC2",M->A2_EST+M->A2_COD_MUN)` ||CC2SA2||||||
14|A2_IBGE|C|11|0|Cod.IBGE|Codigo do IBGE|`@!` |`FS_VLCIDEST(6).and.(vazio().or.ExistCpo("VAM"))` ||AM1|N|A|R|||
15|A2_MUN|C|60|0|Municipio|Municipio do Fornecedor|`@!` ||||N|||||
16|A2_CEP|C|8|0|CEP|Cod Enderecamento Postal|`@R 99999-999` ||||N|||||
17|A2_CX_POST|C|5|0|Caixa Postal|Caixa Postal|`@!` ||||S|||||
18|A2_TIPO|C|1|0|Tipo|Tipo do Fornecedor|`@!` |`pertence("FJX")` |IF(LEFT(SA2->A2_CGC,2) == '  ',' ',IF(LEN(TRIM(SA2->A2_CGC))<14,"F","J"))||N|||F=Fisico;J=Juridico;X=Outros||
19|A2_CGC|C|14|0|CNPJ/CPF|CNPJ/CPF do cliente|`@R 99.999.999/9999-99` |`Vazio() .Or. IIF( M->A2_TIPO == 'X', .T., (CGC(M->A2_CGC) .And. A020CGC(M->A2_TIPO, M->A2_CGC) .And. A020VldUCod()))` |||N|||||
20|A2_PFISICA|C|18|0|RG/Ced.Estr.|Reg.Geral/Ced.Estrangeiro|`@!` |`A020VldUCod()` |||N|||||
21|A2_DDI|C|6|0|DDI|Codigo do DDI|`999999` |`IIF(!EMPTY(M->A2_DDI), ExistCpo("ACJ",M->A2_DDI),.T.)` ||ACJ|S|||||
22|A2_DDD|C|3|0|DDD|Codigo do DDD|`999` ||||N|||||
23|A2_TEL|C|50|0|Telefone|Numero do Telefone|`@R 9999-9999` ||||N|||||
24|A2_FAX|C|15|0|FAX|Numero do FAX do fornec.|`@R 9999-9999` ||||N|||||
25|A2_INSCR|C|18|0|Ins. Estad.|Inscricao Estadual|`@!` |`IE(M->A2_INSCR,M->A2_EST) .And. A020VldUCod()` |||N|||||
26|A2_INSCRM|C|18|0|Ins. Municip|Inscricao Municipal|`@!` ||||N|||||
27|A2_CONTATO|C|15|0|Contato|Contato na Empresa|`@!` ||||N|||||
28|A2_BANCO|C|3|0|Banco|Codigo do Banco|`@!` |||SA6|N|||||
29|A2_AGENCIA|C|5|0|Cod Agencia|Cod Agencia Fornecedor|`@!` ||||N|||||
30|A2_NUMCON|C|10|0|Cta Corrente|Conta Corrente Fornecedor|`@!` ||||N|||||
31|A2_SWIFT|C|30|0|Swift|Swift do Fornecedor|`@!` |||||||||
32|A2_NATUREZ|C|10|0|Natureza|Cod Natureza Financeira|`@!` |`FinVldNat( .T. ,,2)` ||SED|N|||||
33|A2_TRANSP|C|6|0|Transp.|Codigo da Transportadora|`@!` |`vazio().or.existcpo("SA4")` ||SA4|N|||||
34|A2_PRIOR|C|1|0|Prioridade|Prioridade de Pagamento|`9` ||||N|||||
35|A2_RISCO|C|3|0|Risco|Nivel de Risco|`@!` ||||N|||||
36|A2_COND|C|3|0|Cond. Pagto|Condicao de Pagamento|`@!` |`vazio().or.existcpo("SE4")` ||SE4|N|||||
37|A2_LC|C|14|0|Lim. Credito|Limite de Credito|`@!` ||||N|||||
38|A2_MATR|N|4|0|Maior Atraso|Maior Atraso em dias|`9999` ||||N|||||
39|A2_MCOMPRA|N|16|2|Maior Compra|Maior Compra em Valor|`@E 9,999,999,999,999.99` ||||N|V||||
40|A2_METR|N|5|1|Media Atraso|Media de Atraso em dias|`@E 999.9` ||||N|V||||
41|A2_MSALDO|N|16|2|Maior Saldo|Maior Saldo Credor|`@E 9,999,999,999,999.99` ||||N|V||||
42|A2_NROCOM|N|6|0|No Compras|Numero total de Compras|`999999` ||||N|V||||
43|A2_PRICOM|D|8|0|1a Compra|Data da Primeira Compra|||||N|V||||
44|A2_ULTCOM|D|8|0|Ult Compra|Data da ultima Compra|||||N|V||||
45|A2_SALDUP|N|16|2|Sld Duplict|Saldo de Duplicatas|`@E 9,999,999,999,999.99` ||||N|V||||
46|A2_DESVIO|N|6|1|Desvio|Desvio do prz de entrega|`9999.9` ||||N|||||
47|A2_SALDUPM|N|16|2|Sld Moed.For|Saldo em Moeda Forte|`@E 9,999,999,999,999.99` ||||N|V||||
48|A2_CONTA|C|20|0|C Contabil|Codigo da Conta Contabil|`@!` |`vazio().or. Ctb105Cta()` ||CT1|N|||||
49|A2_TIPORUR|C|1|0|Tp.Contr.Soc|Tp.Fornec.ref.Contr.Seg.|`@!` ||||N|||J=Juridico;F=Pessoa Fisica;L=Familiar||
50|A2_RECISS|C|1|0|Recolhe ISS|Recolhe ISS ?|`@!` |`Pertence("SN ")` |||N|||S=Sim;N=Nao||
51|A2_PAIS|C|3|0|Pais|Pais do Fornecedor|`@!` |`Vazio() .or. ExistCpo("SYA",M->A2_PAIS)` ||SYA|N|||||
52|A2_PAISDES|C|25|0|Descr. Pais|Descr. Pais|`@!` ||E_Field("A2_PAIS","YA_DESCR")||N|V|V|||
53|A2_DEPTO|C|30|0|Departamento|Departamento p/ Contato|`@!` ||||N|||||
54|A2_ID_FBFN|C|7|0|Identificac.|Identificacao do Fornec.|`@!` |`ExistCpo("SX5","48"+LEFT(M->A2_ID_FBFN,1))` ||48|N|||||
55|A2_STATUS|C|1|0|Status|Fornecedor Homologado|`9` |`Pertence("12")` |||N|||1=Homologado;2=Nao Homologado||
56|A2_GRUPO|C|3|0|Grupo|Grupo|`@!` |`Vazio().or.ExistCpo("SX5","Y7"+M->A2_GRUPO,1)` ||GRU|N|||||
57|A2_ATIVIDA|C|7|0|Cod.Ativida.|Cod.Atividade Economica|`@!` |||||||||
58|A2_ORIG_1|C|3|0|Origem 1|Origem 1|`@!` |`EicFBOrigem(M->A2_ORIG_1,"1")` ||SYR|N|||||
59|A2_ORIG_2|C|3|0|Origem 2|Origem 2|`@!` |`EicFBOrigem(M->A2_ORIG_2,"2")` ||SYR|N|||||
60|A2_ORIG_3|C|3|0|Origem 3|Origem 3|`@!` |`EicFBOrigem(M->A2_ORIG_3,"3")` ||SYR|N|||||
61|A2_VINCULA|C|1|0|Vinculacao|Tipo Vinculacao|`9` |`Pertence("123")` |"1"||S|||1=Sem Vinculacao;2=Com,Sem Influencia de Preco;3=Com,Com Influencia de Preco||
62|A2_REPRES|C|52|0|Represent.|Representante|`@!S50` ||||N|||||
63|A2_REPCONT|C|50|0|Contato Repr|Contato|`@!` |||||||||
64|A2_REPRTEL|C|50|0|Tel. Repres.|Numero do Telefone|`@!` |||||||||
65|A2_REPRFAX|C|30|0|FAX Repres.|Numero do FAX do Repres.|`@!` |||||||||
66|A2_REPR_EM|C|30|0|E-Mail Repr.|E-Mail Representante||||||||||
67|A2_REPR_EN|C|52|0|End.Repres.|Endereco Representante|`@!S50` ||||N|||||
68|A2_REPBAIR|C|30|0|Bairro Repr.|Bairro do Representante|`@!` ||||N|||||
69|A2_REPRMUN|C|30|0|Cidade|Cidade do Represent.|`@!` |||||||||
70|A2_REPREST|C|2|0|Estado Reprs|Nome do Estado Represent.|`@!` |`Vazio() .or. ExistCpo("SX5","12"+M->A2_REPREST)` ||12||||||
71|A2_REPRCEP|C|8|0|CEP Repres.|Cod Enderecamento Postal|`@R 99999-999` |||||||||
72|A2_REPPAIS|C|3|0|Pais Repres.|Pais do Representante|`@!` |`Vazio() .or. ExistCpo("SYA",M->A2_REPPAIS)` ||SYA||||||
73|A2_ID_REPR|C|1|0|Identif.Repr|Identifica Repres.na L.I.|`!` |`Pertence("12")` |'2'||N|||1=Sim;2=Nao||
74|A2_REPR_BA|C|3|0|Bco. Repres.|Banco do Representate|`@!` |`vazio().or.existcpo("SA6")` ||BCO|N|||||
75|A2_REPR_AG|C|5|0|Agenc. Repr.|Agencia do Representante|`@!` |`Vazio() .or. IF(EMPTY(ALLTRIM(M->A2_REPR_BA)),.T.,ExistCpo("SA6",M->A2_REPR_BA+M->A2_REPR_AG))` ||BC2|N||||`!Empty(M->A2_REPR_BA)` |
76|A2_REPR_CO|C|10|0|C/C Repres.|Conta Corrente Represent.|`@!` ||||N|||||
77|A2_REPRCGC|C|14|0|CNPJ Repres.|CNPJ Representante|`@R 99.999.999/9999-99` |`vazio() .or. cgc(M->A2_REPRCGC)` |||N|||||
78|A2_RET_PAI|C|1|0|Comis.Retida|Comissao Retida no Pais|`!` |`Pertence("12 ")` |||N|||1=Sim;2=Nao||
79|A2_COMI_SO|C|1|0|Tipo Comis.|Tipo Comissao|`9` |`Pertence("1234")` |||N|||1=FOB;2=CFR;3=EX-Works;4=F.A.S.||
80|A2_EMAIL|C|30|0|E-Mail|E-Mail|||||S|||||
81|A2_HPAGE|C|30|0|Home-Page|Home Page|||||S|||||
82|A2_CODMUN|C|5|0|Cod. Mun. ZF|Cod. Mun. ZF Manaus e ALC|`@99999` |`Vazio() .Or. ExistCpo("SX5","S1"+M->A2_CODMUN)` ||S1|N|||||
83|A2_CONTCOM|C|15|0|Contato Com.|Contato Comercial (NNC)|||||N|||||
84|A2_FABRICA|C|1|0|Fabricante|Fabricante|`@!` |`ExistCpo("SX5","48"+LEFT(M->A2_FABRICA,1))` ||48|N|A|R|1=Sim;2=Nao||
85|A2_FATAVA|N|6|2|Fator Aval.|Fator de Avaliacao|`999.99` |`M->A2_FATAVA >= 0.00 .and. M->A2_FATAVA <= 100.00` |||N|||||
86|A2_DTAVA|D|8|0|Data Aval.|Data da Avaliacao|||||N|||||
87|A2_DTVAL|D|8|0|Data Valid.|Data Validade Avaliacao||`M->A2_DTVAL >= M->A2_DTAVA` |A100ReDV()||N|||||
88|A2_OK|C|2|0|OK|OK|||||S|||||
89|A2_RECINSS|C|1|0|Calc. INSS|Calcula INSS p/ Fornec. ?|`@!` |`pertence("SN")` |||N|||S=Sim;N=Nao||
90|A2_TELEX|C|10|0|Telex|Numero do Telex|`@!` ||||N|||||
91|A2_MNOTA|N|16|2|Maior Nota|Maior Nota do Fornecedor|`@E 9,999,999,999,999.99` ||||N|V|R|||
92|A2_CODPAIS|C|5|0|País Bacen|Cód. país Banco Central|`@R 99999` |`ExistCpo("CCH")` ||CCH|N|A|R|||
93|A2_CODLOC|C|8|0|Cod.Local|Codigo da Localidade||`Vazio().Or.ExistCpo("SX5","AB"+M->A2_CODLOC)` |||N|A|R|||
94|A2_TPESSOA|C|2|0|Tipo Pessoa|Tipo de Pessoa|`@!` ||||N|A|R|CI=Comercio/Industria;PF=Pessoa Fisica;OS=Prestacäo de Servico||
95|A2_TPISSRS|C|2|0|Tipo de Escr|Tipo de Escrituração|`99` |`Pertence("01/02/03/04/05/07/08/09/10/11/12/14/15/16/17/18/19")` |||N|A|R|||
96|A2_RECCIDE|C|1|0|Rec Cide|Recolhe CIDE|`@!` |`Pertence("12")` ||||||1=Sim;2=Nao||
97|A2_GRPTRIB|C|3|0|Grp. Tribut.|Grupo de Tributacao|`@!` ||||N|||||
98|A2_UNFEDRP|C|30|0|Unid.Fed.Ext|Unidade Fed. no Exterior|`@!S18` ||||N|||||
99|A2_CONTAB|C|15|0|C.Contab.Imp|Conta Contabil Importação|`@!` ||||N|||||
A0|A2_CLIQF|C|15|0|Liquid.Futur|Liquidacao Futura|`@R 999999999999999` ||||N|||||
A1|A2_PLGRUPO|C|3|0|Classe Forn.|Classe de Fornecedor|`@!` |`Vazio() .Or. ExistCpo("SX5","B9"+M->A2_PLGRUPO)` ||B9|S|||||
A2|A2_CODBLO|C|3|0|Cod.Bloqueio|Codigo do Bloqueio|`@!` ||||N|||||
A3|A2_PAISORI|C|20|0|Pais Origem|Pais de Origem Fornecedor|`@!` ||||N|||||
A4|A2_ROYALTY|C|1|0|Royalty|Royalty|`@!` |`ExistCpo("SX5","H4"+M->A2_ROYALTY)` ||H4||||||
A5|A2_TXTRIBU|N|6|2|TX-BI-Tribut|Taxa de Bi-Tributacao|`@E 999.99` ||||N|||||
A6|A2_B2B|C|1|0|Utiliza B2B|Utiliza B2B?|`@!` |`pertence("12")` |"2"||N|||1=Sim;2=Nao||
A7|A2_PLCRRES|C|1|0|Obrig.Resp|Obrigat. Dig. Resp. Mov ?|`@!` ||"N"|||||S=Sim;N=Nao||
A8|A2_PLFIL|C|1|0|Filial Grupo|Filial do Grupo|`@!` ||"N"|||||S=Sim;N=Nao||
A9|A2_SIGLCR|C|7|0|Sigla C.R|Sigla C.R|`@!` |||||||||
B0|A2_CONREG|C|10|0|Numero C.R|Numero do Conselho Regio.|`@!` |`ExistChav("SA2",M->A2_CONREG+M->A2_SIGLCR,GETMV("MV_PLORDA2")) .And. ExistChav("BA4",M->A2_SIGLCR+M->A2_CONREG,1,"PLASOL")` ||||||||
B1|A2_DATBLO|D|8|0|Data Bloq.|Data do Bloqueio|`@!` |||||V||||
B2|A2_CNAE|C|9|0|Cod CNAE|Codigo CNAE do Fornecedor|`@!` ||||N|A|R||`M->A2_TIPO $ "J,X"` |
B3|A2_CBO|C|7|0|Cod CBO|Codigo CBO do Fornecedor|`@!` ||||N|A|R||`M->A2_TIPO $ "F,X"` |
B4|A2_PLPEDES|N|13|4|% Desc. PLS|% Desconto Producao Med.|`@E 999,999,999.9999` |||||||||
B5|A2_CIVIL|C|1|0|Estado Civil|Estado Civil|`@!` |`naovazio()` |||N|A||1=Solteiro;2=Casado;3=Divorciado;4=Viuvo;5=Companheiro(a);|`M->A2_TIPO = "F"` |
B6|A2_ROYMIN|N|7|2|Royalt Min.|Pagamento minimo Royalty|`9,999.99` ||||N|||||
B7|A2_SATIV1|C|6|0|Segmento 1|Segmentacao de Ativid. 1|`999999` |`ExistCpo("SX5","T3"+M->A2_SATIV1)` ||T3|N|||||
B8|A2_PAGAMEN|C|1|0|Receb.Pagto.|Recebe Pagamento?|`@!` ||||N|||1=Nao;2=Sim||
B9|A2_ENDCOMP|C|21|0|Compl. End.|Complemento Endereco|`@!` ||||N|||||
C0|A2_MSBLQL|C|1|0|Bloqueado|Bloqueia o Fornecedor|`@!` |`pertence("12")` |"2"|||||1=Sim;2=Nao||
C1|A2_GRPDEP|C|5|0|Grupo Almox|Grupo de Almoxarifados|`@!` |`Vazio() .Or. ExistCpo("SX5","74"+M->A2_GRPDEP)` ||74|N|N|R|||
C2|A2_SUBCOD|C|1|0|Sub Codigo|Sub Codigo||||||||||
C3|A2_TIPAWB|C|1|0|Tipo AWB|Tipo AWB|`@!` |`Empty(M->A2_TIPAWB) .Or. ExistCpo("SX5", "MF"+M->A2_TIPAWB)` ||MF|S|||||
C4|A2_DTPAWB|C|30|0|Desc.Tip.AWB|Descricao do Tipo da AWB|`@!` ||IIf(Inclui .Or. Empty(SA2->A2_TIPAWB),"",Tabela("MF", SA2->A2_TIPAWB, .F.))||N|V|V|||
C5|A2_RECSEST|C|1|0|Recolhe SEST|Recolhe SEST|`@!` |`Vazio() .Or. Pertence("12")` ||||||1=Sim;2=Nao||
C6|A2_FILDEB|C|2|0|Fil.Debito|Filial de Debito||`Vazio() .Or. TMSValidEmp(cEmpAnt+M->A2_FILDEB)` ||DLB||||||
C7|A2_RECPIS|C|1|0|Rec. PIS|Recolhimento de PIS|`@!` |`Pertence("12")` |"1"||||R|1=Sim;2=Nao||
C8|A2_RECCOFI|C|1|0|Rec.COFINS|Recolhimento da COFINS|`@!` |`Pertence("12")` |"1"|||||1=Sim;2=Nao||
C9|A2_RECCSLL|C|1|0|Rec.CSLL|Recolhimento da CSLL|`@!` |`Pertence("12")` |"1"|||||1=Sim;2=Nao||
D0|A2_ABICS|C|4|0|Cod. Abics|Cod. Abics|`9999` ||||S|||||
D1|A2_CODFAV|C|6|0|Cod.Favorec|Codigo do Favorecido|`@!` |`Vazio() .Or. ExistCpo("SA2")` ||FOR||||||
D2|A2_LOJFAV|C|2|0|Loja Favorec|Loja do Favorecido|`@!` |`Vazio() .Or. ExistCpo("SA2",M->A2_CODFAV+M->A2_LOJFAV)` ||||||||
D3|A2_NOMFAV|C|40|0|Nome Favorec|Nome do Favorecido|`@!` ||A020NomFav()|||V|V|||
D4|A2_NUMDEP|N|2|0|Dependentes|Nº de Dependentes|`99` |`Positivo()` |||N|A|R|||
D5|A2_CALCIRF|C|1|0|Cálc. IRRF|Cálculo do IRRF.|`9` |`Pertence('1234')` |||N|A|R|1=Normal;2=IRRF Baixa;3=Simples;4=Empresa Individual||
D6|A2_VINCULO|C|2|0|P. Vinculo|Pessoa Vinculada|`@!` |`ExistCpo("CC1")` ||CC1TIP|S|A|R|||
D7|A2_DTINIV|D|8|0|Dt Ini Vincu|Data Inicial do Vinculo|`@!` ||||N|A|R|||
D8|A2_DTFIMV|D|8|0|Dt Fim Vincu|Data Final do Vinculo|||||N|A|R|||
D9|A2_CODADM|C|3|0|Cód. Adm.|Código Adm. Financeira|`@!` |`Vazio() .Or. ExistCpo("SAE")` ||SAE|S|A|R|||
E0|A2_RETISI|C|1|0|Retem ISI|Reten. a taxa de ISI||`Pertence('12')` |"2"|||A|R|1=Sim;2=Nao||
E1|A2_ISICM|C|1|0|Conv. ISI|Conv. Multilateral de ISI||`Pertence('12')` ||||A|R|||
E2|A2_INDRUR|C|1|0|Ind.Prod.Rur|Indicador produtor rural||`Pertence('0123')` |"0"||N|A|R|0=Não é prod.rural;1=Seg.Espec.Geral PF;2=Seg.Espec.Ent.PAA PF;3=Ent.PAA PJ||
E3|A2_UFFIC|C|2|0|UF Ficticia|UF Ficticia|||||N|A|R|ND=Não Declarado;RE=Reexportação;CB=Consumo de Bordo;MN=Mercadoria Nacionalizada|`M->A2_EST == 'EX'` |
E4|A2_TPREG|C|1|0|Tp. Reg|Tipo de Regime|`@!` |`Pertence("12")` |||N|A|R|1=Não Cumulativo;2=Cumulativo||
E5|A2_ISSRSLC|C|1|0|LC ISS RS|LC Enq. ISS|`@!` |`Pertence ("12")` |||N|A|R|1=Sim;2=Não||
E6|A2_SUBCON|C|1|0|SUBCON|SUBCON - Sub Contratista|`@!` |`Pertence("12")` |||S|A|R|1=Sub Contratista;2=Não Sub Contratista||
E7|A2_RFASEMT|C|1|0|Rec.FASE-MT|Recolhe FASE-MT|`@!` |`Pertence(' 12')` ||||A|R|1=Sim;2=Não||
E8|A2_CCICMS|C|1|0|CCICMS|Inscrito no CCICMS|`@!` ||||N|A|R|1=Sim;2=Não||
E9|A2_RIMAMT|C|1|0|Rec. IMA-MT|Recolhe IMA-MT|`@!` |`Pertence(' 12')` ||||A|R|1=Sim;2=Não||
F0|A2_RFUNDES|C|1|0|Rec.FUNDESA|Recolhe FUNDESA.|`@!` |`Pertence(' 12')` ||||A|R|1=Sim;2=Não||
F1|A2_RFABOV|C|1|0|Rec. FABOV|Recolhe FABOV|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Nao||
F2|A2_RFACS|C|1|0|Rec. FACS|Recolhe FACS|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Nao||
F3|A2_RESPTRI|C|2|0|Reg.Esp.Trib|Reg. Esp. de Tributação|`@!` |`ExistCpo("SX5","83"+M->A2_RESPTRI)` ||83|N|A|R|||
F4|A2_TIPCTA|C|1|0|Tp. Cta. For|Tipo de Conta Fornecedor|`@!` |`Pertence("12")` |"1"|||||1=Conta Corrente;2=Conta poupança||
F5|A2_SIMPNAC|C|1|0|Opt Simp Nac|Optante Simples Nacional|`@!` |`Pertence(" 12")` |||S|||1=Sim;2=Não||
F6|A2_SITESBH|C|1|0|SitEspRes BH|Situação Especial de Resp|`@!` |`Pertence(" 1234567")` |||S|||1=Ex Pr bde Ser;2=Pr de Ser c/ Ded;3=Con Civ;4=Ag de Tu/Adm Fun;5=Pro e Pub/Int;6=Pro e Pub/Int Is;7=Não In/Re/Rep||
F7|A2_STRNTRC|C|1|0|Status RNTRC|Status RNTRC|`@!` ||||N|V|R|1=Ativo;2=Inativo||
F8|A2_RECFET|C|1|0|Rec. FETHAB|Recolhe FETHAB|`@!` |`Pertence("12")` |||||R|1=Sim;2=Não||
F9|A2_RECFMD|C|1|0|Rec. Famad|Recolhe FAMAD|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
G0|A2_REGESIM|C|1|0|Rg. Simp. MT|Reg. Simlificado MT|`@!` ||"2"||S|||1=Sim;2=Não||
G1|A2_PAISEX|C|3|0|Codigo Pais|Codigo do Pais pela RFB|`999` |`Vazio() .or. FCkResExt("A2_PAISEX",M->A2_PAISEX)` |||S|A||||
G2|A2_PRSTSER|C|1|0|Ind. Prest.|Ind. Prestador de Serv.|`@!` ||||N||R|||
G3|A2_MJURIDI|C|1|0|M.Jurídico|Disponível mód. Jurídico|`@!` |`Pertence("12")` |"2"||S|A|R|1=Sim;2=Não||
G4|A2_NUMRA|C|6|0|Cód Func|Código do funcionário|`@!` |`ExistCpo("SRA") .And. A020NUMRA(M->A2_NUMRA)` |||N|||||
G5|A2_OCORREN|C|2|0|Ocorrência|Ocorrência SEFIP|`@!` |`FHIST()` |||N|A|R||`FOpOcor()` |
G6|A2_NEMPR|C|150|0|Nome Empres.|Nome Empresarial|`@!` ||||S|A||||
G7|A2_NIFEX|C|30|0|Codigo NIF|No.Identificacao Fiscal|`999999999999999999999999999999` ||||S|A||||
G8|A2_INCULT|C|1|0|Inc. Cultura|Incentivo a Cultura|`@!` |`Pertence(" 12")` |||S|||1=Sim;2=Não||
G9|A2_INDCP|C|1|0|Ind. Rural|Indicativo da opcao rural|`@!` |`Pertence(" 12")` |||N|A|R|1=Sobre a comercializacao da sua producao;2=Sobre a folha de pagamento||
H0|A2_INSCMU|C|1|0|Ins. no Munc|Ins. no Munc. do Tomador|`@!` |`Pertence(" 12")` |||S|||1=Sim;2=Não||
H1|A2_IDHIST|C|20|0|ID Hist.|ID Histórico|`@!` ||||N|V|R|||
H2|A2_IMPIP|C|1|0|Ident.Prod.|Identificacao de Produto|||"2"||N|A|R|1=Pedido Compra;2=Recebimento;3=Nao Imprime;4=Documento Entrada||
H3|A2_FORMPAG|C|2|0|Form. Pgto|Forma de pagamento prefer|`@!` |`ExistCpo("SX5", "58" + M->A2_FORMPAG)` ||58|S|A|R|||
H4|A2_EQPTAC|C|1|0|Equipara TAC|Equipara  a um TAC|`@!` |`Pertence("12")` |||N|V|R|1=Sim;2=Nao||
H5|A2_CALCINP|C|1|0|Calc.INSS.Pt|Calcula INSS Patronal?|`@!` |`Pertence("12")` |||S|A|R|1=Sim;2=Não||
H6|A2_CLIENTE|C|6|0|Cód. Cliente|Código Cliente|`@!` |`ExistCpo("SA1", M->A2_CLIENTE )` ||SA1|S|A|R|||
H7|A2_CATEG|C|2|0|Categ. SEFIP|Categoria para SEFIP|`@` ||||N|A|R|||
H8|A2_CODFI|C|3|0|Cod. FIESP|Código FIESP|||||N|A|R|||
H9|A2_CODINSS|C|11|0|Cód. INSS|Código do INSS|`@!` ||||N|A|R|||
I0|A2_CODNIT|C|11|0|Num Insc Aut|Número Inscrição Autônomo|`@R 9999.9999.999` ||||N|A|R|||
I1|A2_DTNASC|D|8|0|Data nasc.|Data de nascimento|||||N|A|R|||
I2|A2_DTCONV|D|8|0|Dt. Conv|Data do Convite|||||N|A|R|||
I3|A2_DRPEXP|C|8|0|Ident.Exp.|Ident.Exp.Dados|||||N|V|R|||
I4|A2_DESPORT|C|1|0|Assoc. Desp.|Associação Desportiva|`@!` |`Pertence("01")` |||S|A||0=Não;1=Sim||
I5|A2_DEDBSPC|C|1|0|Ded.PIS/COF|Ded. Base de PIS/COFINS|`@!` |`Pertence(' 123456')` |'1'||S|A|R|1=Legado;2=ICMS e IPI;3=ICMS;4=IPI;5=Nenhum;6=Soma IPI||
I6|A2_CPOMSP|C|1|0|Reg. CPOM|Registro CPOM|`@!` |`Pertence("12")` ||||||1=Sim;2=Nao||
I7|A2_CPRB|C|1|0|Ret. CPRB|Indicativo Retenção CPRB|`@!` |`Pertence("12")` |"2"|||||1=Sim;2=Não||
I8|A2_CTARE|C|1|0|Contr TARE ?|Contribuinte TARE ?|`@!` |`Pertence(" 12")` |||S|A|R|1=Sim;2=Nao||
I9|A2_CONTRIB|C|1|0|Contribuinte|Contribuinte do ICMS|`@!` |`Pertence(' 12')` |||N|A|R|1=Sim;2=Não||
J0|A2_CPFIRP|C|11|0|CPF IR Progr|CPF PJ ref IR Progressivo|`@R 999.999.999-99` |`Vazio().Or.(Cgc(M->A2_CPFIRP).And.A020CGC('F',M->A2_CPFIRP))` |||S|A|R||`M->A2_IRPROG == '1'` |
J1|A2_TPRNTRC|C|1|0|Tipo RNTRC|Tipo RNTRC|`@!` ||||N|V|R|1=TAC;2=ETC;3=CTC||
J2|A2_TPJ|C|1|0|TPJ|Tipo de Pessoa Jurídica|`@!` |`Pertence(" 12345")` |||S|||1=ME - Micro Empresa;2=EPP - Empresas de Pequeno Porte;3=MEI - Microempreendedor Individual;4=Cooperativa;5=Não optante||
J3|A2_TPLOGR|C|3|0|Tp. Lograd|Tipo Logradouro|`@!` |||||||||
J4|A2_TPCON|C|2|0|Tipo Contrat|Tipo Contrato|`@!` ||||S|A||||
J5|A2_TPCONTA|C|1|0|Tipo Conta|Tipo de Conta Bancaria|`@!` ||||N|A|R|1=Conta Corrente;2=Poupanca||
J6|A2_TPENT|C|1|0|Clas.PJ|Class. Pessoa Jurídica|`@!` |`Pertence(" 12")` ||||||1=Imune;2=Isento||
J7|A2_TPREX|C|3|0|Rendimento|Tipo do Rendimento|`999` |`Vazio() .or. FCkResExt("A2_TPREX",M->A2_TPREX)` |||S|A||||
J8|A2_TRBEX|C|2|0|Forma Trib.|Forma de Tributação|`99` |`Vazio() .or. FCkResExt("A2_TRBEX",M->A2_TRBEX)` |||S|A||||
J9|A2_TRIBFAV|C|1|0|Pes.Tri.Fav.|Pessoa Trib. Favor.|`@!` |`Pertence (" 12")` |||N|A||1=Sim;2=Não||
K0|A2_CPFRUR|C|11|0|CPF Rural|CPF do produtor rural|`@R 999.999.999-99` |`Iif(FindFunction( "VldRur"), VldRur(), .F.)` |||S|A|R||`Iif(FindFunction( "VldRur"), VldRur(), .F.)` |
K1|A2_CONFFIS|C|1|0|Conf. Física|Indica o local da confe.|`@!` |`Pertence('0123')` |'0'||N|A|R|0=Parâmetro;1=Pré-Nota;2=Nota Fiscal;3=Não utiliza||
K2|A2_DTFIMR|D|8|0|Data Fim|Data Final Contrato||`Vazio() .Or. M->A2_DTFIMR >= M->A2_DTINIR` |CTOD('//')||S|A||||
K3|A2_DTINIR|D|8|0|Data Inicio|Data Inicio Contrato|`@D` ||CTOD('//')||S|A||||
K4|A2_DTRNTRC|D|8|0|Venc. RNTRC|Vencimento RNTRC|||||N|V|R|||
K5|A2_DVAGE|C|1|0|DV Ag Cnab|Digito Verific. Agencia|`@!` |||||||||
K6|A2_DVCTA|C|2|0|DV Cta Cnab|Digito Verificador Conta|`@!` |||||||||
K7|A2_CODSIAF|C|4|0|Cod.Mun.SIAF|Cod.Municipio SIAFI|`@!` ||||N||R|||
K8|A2_COMPLEM|C|50|0|Complemento|Complemento do endereço|`@!` ||||N|A|R|||
K9|A2_COMPLR|C|25|0|Complemento|Complemento Residencial|`@!` ||||S|A||||
L0|A2_CGCEX|C|14|0|CNPJ Empr.Ex|CNPJ Empresa Exterior|`@!R 99.999.999/9999-99` |`Vazio() .or. CGC(M->A2_CGCEX)` |||S|A||||
L1|A2_CIDEX|C|40|0|Cidade|Cidade do Fornecedor|`@!` ||||S|A||||
L2|A2_BREEX|C|3|0|Benef.Rend.|Beneficiario Rendimento|`999` |`Vazio() .or. FCkResExt("A2_BREEX",M->A2_BREEX)` |||S|A||||
L3|A2_CARGO|C|40|0|Cargo Resp.|Cargo Responsavel|`@!` ||||S|A|R|||
L4|A2_BAIEX|C|20|0|Bairro/Dist.|Bairro/Distrito do Func.|`@!` |||||||||
L5|A2_APOLICE|C|20|0|Num. Apolice|Num. Apolice|`@!` ||||S|A|R|||
L6|A2_ENDNOT|C|1|0|End.Not.Form|Endereço não formatado|`@!` |`Pertence(" 12")` |||S|A|R|1=Sim;2=Não||
L7|A2_ESTEX|C|40|0|Est./Prov.|Estado/Provindia do Func.|`@!` ||||S|A||||
L8|A2_FORNEMA|C|1|0|Forn.Mailing|Fornecedor de Mailing|`@!` |`Pertence("12")` |"2"||N|A|R|1=Sim;2=Não||
L9|A2_FRETISS|C|1|0|F.Ret.ISS|Forma retenção ISSQN|`@!` |`Pertence(' 12')` |||N|A|R|1=Valor mínimo;2=Sempre retém||
M0|A2_FILTRF|C|2|0|Fil. Transf.|Filial para transferência||`Vazio() .Or. IIF(FindFunction('MtValidFil'),MtValidFil(cEmpAnt+M->A2_FILTRF),.T.)` ||DLB|S|A|R|||
M1|A2_FOMEZER|C|1|0|Fome Zero|Participação no Fome Zero|`@!` |`Pertence(" 12")` |||S|A|R|1=Sim;2=Não||
M2|A2_INCLTMG|C|1|0|Inc.Prd.Leit|Incentivo Prod.Leite-MG|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Não||
M3|A2_IRPROG|C|1|0|IRRF Prog|Calcula IRRF Progressivo|`@!` |`Pertence(" 12")` |||N|A|R|1=Sim;2=Nao||
M4|A2_INOVAUT|C|1|0|Inovar Auto|Inovar Auto|`@!` |`Pertence(" 123")` |"2"||N|A|R|1=Participa;2=Não Participa;3=Convidar||
M5|A2_MUNSC|C|5|0|Cod Mun SC|Codigo do Municipio de SC||||||A|R|||
M6|A2_NOMRESP|C|45|0|Nome Resp.|Nome do Responsavel|||||N|A|R|||
M7|A2_NUMEX|C|6|0|Numero|Numero da Residencia|`@!` ||||S|A||||
M8|A2_LOJCLI|C|2|0|Loja Cliente|Loja Cliente|`@!` |`ExistCpo("SA1", M->A2_CLIENTE + M->A2_LOJCLI )` |||S|A|R|||
M9|A2_MOTNIF|C|1|0|Mot.NIF|Mot. N.Preench NIF|||"1"|||A|R|1=Dispensado do NIF;2=País não exige NIF||
N0|A2_MSBLQD|D|8|0|BlqTemporal|Bloqueio Temporal|||||N|A|R|||
N1|A2_LOCQUIT|C|1|0|Local Quitac|Local de Quitacao|`@!` |`Vazio() .Or. Pertence('01')` |||N|A|R|0=Filial;1=Posto||
N2|A2_LOGEX|C|60|0|Logradouro|Logradouro do Fornecedor|`@!` ||||S|A||||
N3|A2_MINIRF|C|1|0|Vlr. Min. IR|Valor Mínimo de IRRF|`@!` |`Pertence("12")` |"2"||N|A|R|1=Sim;2=Nao||
N4|A2_MINPUB|C|1|0|Vl. Mín. Pub|Valor Mín. PCC e IR EmPub|`@!` |`Pertence('12')` |"2"|||A|R|1=Sim; 2=Não;||
N5|A2_POSEX|C|10|0|Cod.Postal|Cod.Postal Fornecedor|`@!` ||||S|A||||
N6|A2_PAGGFE|C|1|0|Pagto GFE|Pagamento pelo SIGAGFE|`@!` |`Pertence("12")` |"2"||N|A|R|1=Sim;2=Nao||
N7|A2_REGPB|C|1|0|Reg.Paraíba|Regime Paraíba|`@!` |`Pertence(" 12" )` |||N|A|R|1=Sim;2=Não||
N8|A2_TELRE|C|15|0|Telefone|Numero do Telefone|`@!` ||||S|A||||
N9|A2_RNTRC|C|14|0|RNTRC|Reg. Nac. Tr. Rod. Cargas|`@9` ||||N|A|R|||


## SIX - Índices da tabela

ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|A2_FILIAL+A2_COD+A2_LOJA|Codigo + Loja|||S|
2|A2_FILIAL+A2_NOME+A2_LOJA|Razao Social + Loja|||S|
3|A2_FILIAL+A2_CGC|CNPJ/CPF|||S|
4|A2_FILIAL+A2_ID_FBFN|Identificac.|||S|
5|A2_FILIAL+A2_CONREG+A2_SIGLCR|Numero C.R + Sigla C.R|||S|
6|A2_FILIAL+A2_VINCULO|P. Vinculo|CC1||S|
7|A2_FILIAL+A2_NUMRA|Cód Func|||S|
8|A2_FILIAL+A2_CODADM|Cód. Adm.|||S|
9|A2_FILIAL+A2_IDHIST|ID Hist.|||S|
A|A2_FILIAL+A2_CONTA|C Contabil|||S|


