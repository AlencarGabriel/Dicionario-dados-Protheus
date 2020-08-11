# SE2 - Contas a Pagar
## SX3 - Campos da tabela

X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|E2_FILIAL|C|2|0|Filial|Filial do Sistema|||||N|||||
02|E2_PREFIXO|C|3|0|Prefixo|Prefixo do Titulo|`@!` |`FA050Num()` |||S|||||
03|E2_NUM|C|9|0|No. Titulo|Numero do Titulo|`@!` |`FA050Num()` |||S|||||
04|E2_PARCELA|C|2|0|Parcela|Parcela do Titulo|`@!` |`FA050Num()` |||S|||||
05|E2_TIPO|C|3|0|Tipo|Tipo do Titulo|`@!` |`FA050Tipo() .and. FA050Num() .and. FA050Natur()` ||05|S|||||
06|E2_NATUREZ|C|10|0|Natureza|Codigo da natureza|`@!` |`FA050Natur().and.FinVldNat( .F., M->E2_NATUREZ, 2 )` ||SED|S|||||
07|E2_PORTADO|C|3|0|Portador|Codigo do portador|`@!` |||BCO|S|||||
08|E2_FORNECE|C|6|0|Fornecedor|Codigo do Fornecedor|`@!` |`ExistCpo("SA2",M->E2_FORNECE,,,,.F.).and. fa050num() .and. FreeForUse("SE2",M->E2_NUM+M->E2_FORNECE)` ||FOR|S|||||
09|E2_LOJA|C|2|0|Loja|Loja do Fornecedor|`@!` |`Iif(Vazio(), .T., ExistCpo("SA2",M->E2_FORNECE+M->E2_LOJA)) .and. fa050num() .and. FA050NATUR()` |||S|||||
10|E2_NOMFOR|C|20|0|Nome Fornece|Nome do fornecedor|`@!` ||||N|V||||
11|E2_EMISSAO|D|8|0|DT Emissao|Data de Emissao do Titulo||`iif(Empty(m->e2_vencto),.T.,m->e2_emissao <= m->e2_vencto)` |ddatabase||S|||||
12|E2_VENCTO|D|8|0|Vencimento|Vencimento do Titulo||`FA050Venc()` |||S|||||
13|E2_VENCREA|D|8|0|Vencto Real|Vencimento real do Titulo||`m->e2_vencrea>=m->e2_vencto .AND. FA050Venc(2)` |||S|||||
14|E2_VALOR|N|16|2|Vlr.Titulo|Valor do Titulo|`@E 9,999,999,999,999.99` |`positivo().and.naovazio().and.FA050Nat2().and.fa050valor()` |||S|||||
15|E2_ISS|N|14|2|ISS|Valor do ISS|`@E 99,999,999,999.99` |`positivo() .and. m->e2_iss  < m->e2_valor .and. IIF(m->e2_tipo="PR" .and. m->e2_iss > 0,.F.,.T.) .and. fa050iss()` |||N||||`M->E2_MULTNAT != "1"` |
16|E2_IRRF|N|14|2|IRRF|Valor do IRRF|`@E 99,999,999,999.99` |`positivo() .and. m->e2_irrf < m->e2_valor .and. IIF(m->e2_tipo="PR" .and. m->e2_irrf>0,.F.,.T.) .and. fa050irr()` |||S||||`M->E2_MULTNAT != "1"` |
17|E2_NUMBCO|C|15|0|Nº do Cheque|Numero do Cheque|`@!` ||||N|||||
18|E2_INDICE|C|3|0|Reajuste|Cod da Tabela de Reajuste|`@!` ||||N|||||
19|E2_BAIXA|D|8|0|DT Baixa|Data de Baixa do Titulo|||dDataBase||S|||||
20|E2_BCOPAG|C|3|0|Bco de Pgto|Banco de pagamento|`@!` |`existcpo("SA6")` ||BCO|N|||||
21|E2_EMIS1|D|8|0|DT Contab.|Data de Contabilizacao|||||N|||||
22|E2_HIST|C|40|0|Historico|Historico do Título|`@!` ||||S|||||
23|E2_LA|C|1|0|Ident. Lanc.|Identificador de LA    .|`@!` ||||N|||||
24|E2_LOTE|C|4|0|Lote Contabl|Lote Contabil|`@!` ||||N|||||
25|E2_MOTIVO|C|20|0|Motivo|Motivo do nao pagamento|`@!` ||||N|||||
26|E2_MOVIMEN|D|8|0|Ult.Moviment|Data da ultima movimentac|||||N|||||
27|E2_OP|C|14|0|Ord Producao|Ordem de producao|`@9` |`vazio().or.existcpo("SC2")` ||SC2|N|||||
28|E2_SALDO|N|16|2|Saldo|Saldo a Receber|`@E 9,999,999,999,999.99` ||||S|||||
29|E2_OK|C|2|0|Ident.Baixa|Ident.Baixa Automatica|||||N|||||
30|E2_DESCONT|N|16|2|Desconto|Valor do Desconto|`@E 9,999,999,999,999.99` ||||N|||||
31|E2_MULTA|N|16|2|Multa|Valor da Multa|`@E 9,999,999,999,999.99` ||||N|||||
32|E2_JUROS|N|16|2|Juros|Valor do Juros|`@E 9,999,999,999,999.99` ||||S|||||
33|E2_CORREC|N|16|2|Correcao|Valor da Correcao|`@E 9,999,999,999,999.99` ||||N|||||
34|E2_VALLIQ|N|16|2|Val Liq Baix|Valor Liquido da Baixa|`@E 9,999,999,999,999.99` ||||N|||||
35|E2_VENCORI|D|8|0|Vencto Orig|Vencimento Original|||||N|||||
36|E2_VALJUR|N|14|2|Taxa Perman.|Taxa Permanencia Diaria|`@E 99,999,999,999.99` |`positivo() .and. m->e2_valjur < m->e2_valor` |||S|||||
37|E2_PORCJUR|N|5|2|Porc Juros|Porcentual Juros Diario|`@E 99.99` ||||S|||||
38|E2_MOEDA|N|2|0|Moeda|Moeda do Titulo|`99` |`fa050moed().and.Fa050Nat2().And.FA050VALOR()` |1||S|||||
39|E2_NUMBOR|C|6|0|Num Bordero|Numero do Bordero|`@!` ||||S|||||
40|E2_FATPREF|C|3|0|Pref. Fatura|Prefixo fatura gerada|`@!` ||||N|||||
41|E2_FATURA|C|9|0|Num Fatura|Numero da Fatura|`@!` ||||N|||||
42|E2_PROJETO|C|6|0|Projeto|Codigo do Projeto||`vazio().or.ExistCPO("SX5","52"+M->E2_PROJETO)` ||52|N|||||
43|E2_CLASCON|C|5|0|Classific.|Classificacao||`vazio().or.ExistCPO("SX5","51"+M->E2_CLASCON)` ||51|N|||||
44|E2_RATEIO|C|1|0|Rateio|Rateio Centro Custo|`@!` |`pertence("SN")  .And. If(M->E2_RATEIO="S".And. GetMv("MV_MCONTAB")="CTB",(F050EscRat("511","FINA050",cLote),.T.),.T.)` |"N"||N|||S=Sim;N=Nao|`F050RatDes(2)` |
45|E2_DTVARIA|D|8|0|Dt.Ult.Var.|Data da Ultima Variacao|||||N|||||
46|E2_VARURV|N|16|2|Vl.Var.Acum.|Valor da Variacao Acumul.|`@E 9,999,999,999,999.99` ||||N|||||
47|E2_VLCRUZ|N|16|2|Vlr R$|Valor na moeda nacional|`@E 9,999,999,999,999.99` ||||N|||||
48|E2_DTFATUR|D|8|0|Data Faturam|Data Faturamento|||||N|||||
49|E2_ACRESC|N|16|2|Acrescimo|Valor de Acrescimo|`@E 9,999,999,999,999.99` |`POSITIVO().AND.M->E2_DECRESC==0.AND.iiF(INCLUI,.T.,SE2->E2_SALDO>0).OR.FINVLACDC('P')` |||N||||`!(MVPAGANT == M->E2_TIPO )` |
50|E2_TITORIG|C|50|0|Tit. Origem|Nº Título Origem Vendor|`@!` ||||N|||||
51|E2_IMPCHEQ|C|1|0|Imp.Cheque|Flag Imp Cheque|||||N|||||
52|E2_PARCIR|C|2|0|Parc. IRF|Parcela do IRF|`@!` ||||N|||||
53|E2_ARQRAT|C|30|0|Arq Rateio|Nome do Arquivo de Rateio|`@!` ||||N|||||
54|E2_OCORREN|C|2|0|Ocorr CNAB|Codigo Ocorrencia CNAB|`!!` ||"01"||N|||||
55|E2_ORIGEM|C|8|0|Origem|Origem do Título|||||N|||||
56|E2_IDENTEE|C|6|0|Ident CEC|Ident Comp Entre Carteira|`@!` ||||N|V||||
57|E2_FLUXO|C|1|0|Fluxo Caixa|Fluxo de Caixa|`@!` |`pertence("SN")` |"S"|||||S=Sim;N=Nao||
58|E2_PARCISS|C|2|0|Parc ISS|Parcela do ISS|`@!` ||||N|||||
59|E2_ORDPAGO|C|6|0|Ordem Pagto|Numero da Ordem de Pagto|`@!` |||||||||
60|E2_DESDOBR|C|1|0|Desdobramen.|Desdobramento|`@!` |`IIF(M->E2_DESDOBR=="S",F050dsdobr(),.T.) .And. M->E2_DESDOBR $ "SN"` |'N'||N|||S=Sim;N=Nao|`F050RatDes(3)` |
61|E2_INSS|N|14|2|INSS|Valor do INSS|`@E 99,999,999,999.99` |`positivo() .and. M->E2_INSS<M->E2_VALOR .and. iif(M->E2_INSS>0 .and. M->E2_TIPO == "PR ", .f. , .t.) .and. FA050INSS()` |||S||||`M->E2_MULTNAT != "1"` |
62|E2_PARCINS|C|2|0|Parc. INSS|Parcela do INSS|`@!` ||||N|||||
63|E2_NUMLIQ|C|6|0|No.Liquidaç.|Número da Liquidação|`@!` |||||||||
64|E2_BCOCHQ|C|3|0|Bco Cheque|Banco Cheque Liquidac.|`@!` ||||N|||||
65|E2_AGECHQ|C|5|0|Agência Cheq|Agência Cheque Liquidac.|`@!` ||||N|||||
66|E2_CTACHQ|C|10|0|Cta Cheque|Conta Cheque Liduidac.|`@!` ||||N|||||
67|E2_DATALIB|D|8|0|Dt Liberacao|Data da Liberacao|||||S|||||
68|E2_APROVA|C|20|0|Aprovador|Liberador do titulo|`@!` ||||S|||||
69|E2_TIPOFAT|C|3|0|Tipo Fatura|Tipo da Fatura|`@!` ||||N|||||
70|E2_FLAGFAT|C|1|0|Flag Faturas|Flag Faturas|`@!` ||||N|||||
71|E2_ANOBASE|C|4|0|Ano Base|Ano Base|`@!` ||||N|||||
72|E2_MESBASE|C|2|0|Mes Base|Mes Base|`@!` ||||N|||||
73|E2_TXMOEDA|N|11|4|Taxa moeda|Taxa da moeda|`@E 999999.9999` |`positivo()` |||N||||`WTxMoe(M->E2_MOEDA)` |
74|E2_SDACRES|N|16|2|Sld.Acresc.|Saldo do Acrescimo|`@E 9,999,999,999,999.99` ||||N|||||
75|E2_DECRESC|N|16|2|Decrescimo|Valor de Decrescimo|`@E 9,999,999,999,999.99` |`(M->E2_DECRESC<M->E2_VALOR).AND.POSITIVO().AND.M->E2_ACRESC==0.AND.IIF(INCLUI,.T.,SE2->E2_SALDO>0).OR.FINVLACDC('P')` |||N||||`!(MVPAGANT == M->E2_TIPO )` |
76|E2_SDDECRE|N|16|2|Sld.Decresc.|Saldo do Decrescimo|`@E 9,999,999,999,999.99` ||||N|||||
77|E2_USUALIB|C|25|0|Usuario|Nome do Usuario|||||S|||||
78|E2_MULTNAT|C|1|0|Mult. Natur.|Multiplas naturezas p/Tit||`pertence("12") .And. Fa050MultNat()` |"2"||N|||1=Sim;2=Nao|`F050RatDes(1)` |
79|E2_NUMTIT|C|50|0|Tit IRRF Off|Nro Titulo IR off line|`@!` |||||||||
80|E2_PROJPMS|C|1|0|Rateio Proj.|Rateio de Projetos|||"2"||N|V||1=Sim;2=Nao||
81|E2_PLLOTE|C|10|0|Lote PLS|Numero do Lote PLS|`@!` ||||N|||||
82|E2_DIRF|C|1|0|Gera Dirf|Gera Dirf para este tit?|`!` |`pertence("12")` |"2"||N|||1=Sim;2=Nao||
83|E2_CODRET|C|4|0|Cd. Retenção|Codigo de Retencao|`9999` |`EXISTCPO("SX5","37"+M->E2_CODRET) .AND. Iif(FUNNAME() $ "FINA050|FINA750",FA050Natur(),.T.)` ||37|S||||`M->E2_DIRF=="1"` |
84|E2_MODSPB|C|1|0|Mod. Pagto.|Modalidade Pagto.Previsto|`@!` |`Pertence("123") .and. SPBTIPO("SE2")` |"1"||S|||1=TED;2=CIP;3=COMP|`SpbInUse()` |
85|E2_IDCNAB|C|10|0|Id. Cnab|Identificador Cnab|`@!` ||||N|||||
86|E2_PARCCSS|C|2|0|Parc.CSS|Parcela do Funrural|`@!` |||||||||
87|E2_RETENC|N|16|2|Vl Retencao|Valor de Retencão|`@E 9,999,999,999,999.99` |`Positivo() .and. M->E2_RETENC>E2_VALOR` ||||||||
88|E2_CONTAD|C|20|0|Cta.Contabil|Conta Contabil||`Vazio() .or. CTB105CTA()` ||CT1||||||
89|E2_CODORCA|C|8|0|Cod. Orcam.|Codigo do Orcamento|||||S|||||
90|E2_DOCHAB|C|6|0|DH|Documento Hábil|`@!` ||||N|V|R|||
91|E2_SEST|N|14|2|SEST/SENAT|SEST/SENAT|`@E 99,999,999,999.99` |`Positivo() .And. Fa050SEST()` |||||||`M->E2_MULTNAT != "1"` |
92|E2_PARCSES|C|2|0|Parc.SEST|Parcela do SEST|`@!` |||||||||
93|E2_FILDEB|C|2|0|Fil.Debito|Filial de Debito||||||||||
94|E2_FILORIG|C|2|0|Filial Orig.|Filial de origem||`VldFilOrig(M->E2_FILORIG)` |||N|||||
95|E2_FORNISS|C|6|0|Fornec ISS|Cod Fornecedor ISS|`@!` |||FOR||||||
96|E2_LOJAISS|C|2|0|Lj Forn ISS|Loja do Fornecedor ISS|`@!` |||||||||
97|E2_DEBITO|C|20|0|Conta Deb.|Conta a Debito|`@!` |`Vazio() .or. CTB105CTA()` ||CT1|N|A|R|||
98|E2_CCD|C|9|0|C.Custo Deb.|C.Custo a Debito|`@!` |`Vazio() .or. CTB105CC()` ||CTT|N|A|R|||
99|E2_ITEMD|C|9|0|Item Ctb.Deb|Item Contabil a Debito|`@!` |`Vazio() .or. CTB105ITEM()` ||CTD|N|A|R|||
A0|E2_CLVLDB|C|9|0|Cl.Vlr. Deb.|Classe de Valor a Debito|`@!` |`Vazio() .or. CTB105CLVL()` ||CTH|N|A|R|||
A1|E2_CREDIT|C|20|0|Conta Cred.|Conta Contabil a Credito|`@!` |`Vazio() .or. CTB105CTA()` ||CT1|N|A|R|||
A2|E2_CCC|C|9|0|C.Custo Cred|C.Custo a Credito|`@!` |`Vazio() .or. CTB105CC()` ||CTT|N|A|R|||
A3|E2_ITEMC|C|9|0|Item Ctb Crd|Item Contabil a Credito|`@!` |`Vazio() .or. CTB105ITEM()` ||CTD|N|A|R|||
A4|E2_CLVLCR|C|9|0|Cl.Vlr. Cred|Classe de Valor a Credito|`@!` |`Vazio() .or. CTB105CLVL()` ||CTH|N|A|R|||
A5|E2_COFINS|N|14|2|COFINS|Valor COFINS|`@E 99,999,999,999.99` |`positivo() .and. m->e2_cofins < m->e2_valor .and. IIF(m->e2_tipo="PR" .and. m->e2_cofins>0,.F.,.T.) .and. fa050Cofins()` ||||||||
A6|E2_PIS|N|14|2|PIS/PASEP|Valor PIS|`@E 99,999,999,999.99` |`positivo() .and. m->e2_pis < m->e2_valor .and. IIF(m->e2_tipo="PR" .and. m->e2_pis>0,.F.,.T.) .and. fa050Pis()` ||||||||
A7|E2_CSLL|N|14|2|CSLL|Valor CSLL|`@E 99,999,999,999.99` |`positivo() .and. m->e2_csll < m->e2_valor .and. IIF(m->e2_tipo="PR" .and. m->e2_csll>0,.F.,.T.) .and. fa050Csll()` ||||||||
A8|E2_PARCCOF|C|2|0|Parc. COFINS|Parcela do Cofins|`@!` ||||N|||||
A9|E2_PARCPIS|C|2|0|Parc. PIS|Parcela do PIS|`@!` ||||N|||||
B0|E2_PARCSLL|C|2|0|Parc. CSLL|Parcela do CSLL|`@!` ||||N|||||
B1|E2_TITPIS|C|50|0|Titulo PIS|Num do titulo orig do PIS||||||||||
B2|E2_TITCOF|C|50|0|Tit COFINS|No. Tit origem do COFINS||||||||||
B3|E2_TITCSL|C|50|0|Titulo CSLL|No. tit. origem CSLL||||||||||
B4|E2_TITINS|C|50|0|Titulo INSS|Titulo INSS off line||||||||||
B5|E2_VRETPIS|N|14|2|Valor Rt.Pis|Valor retido - PIS|`@E 99,999,999,999.99` |||||V||||
B6|E2_VRETCOF|N|14|2|Valor Rt.Cof|Valor retido - COFINS|`@E 99,999,999,999.99` |||||V||||
B7|E2_VRETCSL|N|14|2|Valor Rt CSL|Valor Retido - CSLL|`@E 99,999,999,999.99` |||||V||||
B8|E2_PRETPIS|C|1|0|Pend.Rt.PIS|Pendente Retencao - PIS||||||V||||
B9|E2_PRETCOF|C|1|0|Pend.Rt.COF|Pendente Retencao -COFINS||||||V||||
C0|E2_PRETCSL|C|1|0|Pend.Rt.CSLL|Pendente Retencao - CSLL||||||V||||
C1|E2_SEQBX|C|2|0|Seq.Baixa|Sequencia da Baixa|`@!` ||||N|V||||
C2|E2_CODBAR|C|44|0|Cod.Barras|Codigo de Barras||`Vazio() .OR. VldCodBar(M->E2_CODBAR)` |||N|A|R|||
C3|E2_LINDIG|C|48|0|Linha Dig.|Linha Digitável||`Vazio() .OR. VldCodBar(M->E2_LINDIG)` ||||||||
C4|E2_BASEPIS|N|16|2|Base PCC|Base do PCC|`@E 9,999,999,999,999.99` |`positivo() .and. fa050nat2()` |||N|A|R||`If(FindFunction('F050BSIMP'),F050BSIMP(1,2),.f.)` |
C5|E2_BASECSL|N|16|2|Base Csll|Base Csll ref ao titulo|`@E 9,999,999,999,999.99` |`positivo() .and. fa050nat2()` |||N|V|R||`If(FindFunction('F050BSIMP'),F050BSIMP(1,4),.f.)` |
C6|E2_VRETISS|N|14|2|Valor Rt.ISS|Valor Retido - ISS|`@E 99,999,999,999.99` |||||V||||
C7|E2_VENCISS|D|8|0|Venc.ISS|Vencimento ISS|||||N|A|R|||
C8|E2_VBASISS|N|15|2|Vlr.Ac.Serv.|Valor Acumulado Serviços|`@E 999,999,999,999.99` ||||N|V|R|||
C9|E2_MDRTISS|C|1|0|Mod.Ret.ISS|Modo de Retenção de ISS|`@!` |`Pertence("12")` |"1"||N|A|R|1=Normal;2=Por Base||
D0|E2_VARIAC|N|2|0|Variac. DCTF|Variação conf.Cod.Rec.|`@E 99` ||||N|A|R|||
D1|E2_PERIOD|C|1|0|Period. DCTF|Periodicidade cod. DCTF|`@!` |`Pertence("DSXQMBTUEA")` ||||||||
D2|E2_MDCONTR|C|15|0|Num.Contrato|Numero do contrato|`@!` ||||N|V|R|||
D3|E2_MDREVIS|C|3|0|Revisão cont|Revisão do contrato|`@!` ||||N|V|R|||
D4|E2_MDPLANI|C|6|0|Num. Planilh|Numero da Planilha|`@!` ||||N|V|R|||
D5|E2_MDCRON|C|6|0|Num. Cronogr|Numero do Cronograma|`@!` ||||N|V|R|||
D6|E2_MDPARCE|C|2|0|Num. Parcela|Numero da Parcela|`@!` ||||N|V|R|||
D7|E2_FRETISS|C|1|0|Form Ret ISS|Forma de retenção do ISS|`@!` |`PERTENCE("12") .and. FA050NAT2()` |"1"||N|A|R|1=Cons.Vlr.Min.;2=Sempre retém||
D8|E2_TXMDCOR|N|14|4|Tx Cor.Moeda|Tx. Moeda na Correcao M.|`@E 999,999,999.9999` |||||||||
D9|E2_APLVLMN|C|1|0|Aplic.Vl.Min|Aplica Vlr. Mínimo|`@!` |`pertence("12")` |"1"|||||1=Sim;2=Não||
E0|E2_CLEARIN|C|3|0|Cod.Clearing|Codigo do Clearing SPB|`@!` |||||||||
E1|E2_HORASPB|C|5|0|Hora SPB|Hora do Agendamento SPB|`"99:99"` |||||V||||
E2|E2_PRETIRF|C|1|0|Pend.Ret IRF|Pendente de Retenção - IR||||||V||||
E3|E2_SEFIP|C|1|0|SEFIP|SEFIP||||||V||||
E4|E2_TRETISS|C|1|0|Retencao ISS|Retenção do ISS||||||V||||
E5|E2_VRETIRF|N|14|2|Valor Rt. IR|Valor Retido - IRRF|`@E 99,999,999,999.99` |||||V||||
E6|E2_PLOPELT|C|4|0|Operadora Lt|Operadora Lote Pagto|`@!` |||||V|R|||
E7|E2_CODRDA|C|6|0|Cod. Rda|Codigo Rede Atendimento|`@!` |||||||||
E8|E2_PARCFET|C|2|0|Parc.FETHAB|Parcela do Imposto FETHAB|`@!` |||||||||
E9|E2_FETHAB|N|14|2|Vlr.FETHAB|Valor do Imposto FETHAB|`@E 99,999,999,999.99` |||||||||
F0|E2_FORORI|C|6|0|Forn.Orig.|Fornecedor Original|`@!` |||||V|R|||
F1|E2_LOJORI|C|2|0|Loja Orig|Loja Original|`@!` |||||V|R|||
F2|E2_STATUS|C|1|0|Status|Status|||||N|||||
F3|E2_DTDIRF|D|8|0|Dt Ger. Dirf|Data de Geracao da Dirf||||||||||
F4|E2_TITADT|C|50|0|Titulo Adt|Titulo Adto do PA Bruto|||||N|A|R|||
F5|E2_TITPAI|C|50|0|Titulo Pai|Titulo Pai do Imposto|||||N|A|R|||
F6|E2_INSSRET|N|6|2|INSS Retido|INSS Retido|`@E 999.99` |`Positivo()` |||N|A|R|||
F7|E2_CODAGL|C|6|0|Cód. Aglut.|Código Aglutinador|`@!` ||||N|A|R|||
F8|E2_PROCPCC|C|9|0|Processo PCC|Nro. Processo PCC|`@!` ||||N|A|R|||
F9|E2_FORNPAI|C|50|0|Forn.Pai PCC|Fornec.Titulo Pai PCC|||||N|A|R|||
G0|E2_CODISS|C|6|0|Cod.Aliq.ISS|Codigo Aliquota ISS|`@9` |`ExistCpo( 'FIM', M->E2_CODISS ).AND.FA050Nat2().and.fa050valor()` ||FIM|N|A|R|||
G1|E2_USUASUS|C|25|0|Usuário|Nome do Usuário|`@!` ||||N|A|R|||
G2|E2_USUACAN|C|25|0|Usuario|Nome do usuario|`@!` ||||N|A|R|||
G3|E2_DATASUS|D|8|0|Dt Suspensão|Data da Suspensão|||||N|A|R|||
G4|E2_DATACAN|D|8|0|Dt Cancel.|Data do Cancelamento|||||S|A|R|||
G5|E2_LIMCAN|D|8|0|Dt.Lim.Canc|Dt Limite do Cancelamento|||||N|A|R|||
G6|E2_FORBCO|C|3|0|Banco For.|Banco do Fornecedor|`@!` |||FIL|N|A|R|||
G7|E2_FORAGE|C|5|0|Agencia For.|Agencia Bancaria Fornec.|`@!` ||||N|A|R|||
G8|E2_FAGEDV|C|1|0|DV Agencia|Digito Verificador Agenc.|`@!` ||||N|A|R|||
G9|E2_FORCTA|C|10|0|Conta For.|Conta do Fornecedor|`@!` ||||N|A|R|||
H0|E2_FCTADV|C|2|0|DV Conta|Digito Verificador Conta|`@!` ||||N|A|R|||
H1|E2_PREOP|C|6|0|Pre-ordem|Pre-Ordem de Pago|`@!` ||||N|V|R|||
H2|E2_DTAPUR|D|8|0|Dt. Apuração|Data de apuração|||||N|A|R||`M->E2_DIRF == "1"` |
H3|E2_NROREF|C|15|0|Referencia|Numero de Referencia|`@!` ||||N|A|R||`M->E2_DIRF == "1"` |
H4|E2_NOMERET|C|60|0|Contribuinte|Nome do Contribuinte|`@!` ||||N|V|R|||
H5|E2_TPINSC|C|1|0|Tp.Inscrição|Tipo de Inscricao do Cont|`@!` ||||N|V|R|||
H6|E2_PARCIMA|C|2|0|Parc. IMA|Parcela do Imposto IMA|`@!` ||||N|A|R|||
H7|E2_IMA|N|14|2|Valor IMA|Valor do Imposto IMA|`@E 99,999,999,999.99` ||||N|A|R|||
H8|E2_BASEISS|N|16|2|Base ISS|Base ISS|`@E 9,999,999,999,999.99` |`positivo() .and. fa050nat2()` |||N|A|R||`If(FindFunction('F050BSIMP'),F050BSIMP(1,6),.f.)` |
H9|E2_NUMPRO|C|10|0|Proc. Refer.|Nro Proc. Referenciado|`@!` |`Vazio().Or.ExistCpo('CCF')` ||CCF|N|A|R|||
I0|E2_INDPRO|C|1|0|Tp. Processo|Tipo de Processo|`@!` |`Pertence("01239")` |||N|A|R|0=Sefaz;1=Justiça Federal;2=Justiça Estadual;3=Secex/SRF;9=Outros||
I1|E2_IDMOV|C|10|0|Id. Mov.|Id. Movimento|`@!` ||||N|V|R|||
I2|E2_FORMPAG|C|2|0|Forma Pgto.|Forma de pagamento Prefer|`@!` |`If( !Empty(M->E2_FORMPAG) ,ExistCpo("SX5", "58" + M->E2_FORMPAG), .T. )` ||58|S|A|R|||
I3|E2_FMPEQ|N|16|2|Vl.FUMIPEQ|Valor do Fumipeq|`@E 9,999,999,999,999.99` ||||N|A|R|||
I4|E2_FIMP|C|1|0|Flag Imp NFe|Flag de Impressão NFe|`@!` ||||N|A|R|||
I5|E2_ITEMCTA|C|9|0|Item Contab.|Item Contabil|`@!` |`(Vazio() .OR. Ctb105Item())` ||CTD|N|A|R||`CtbInUse()` |
I6|E2_MDBONI|N|15|2|Bonific Ctr|Bonificação de Contrato|`@E 999,999,999.99` ||0||N|A|R|||
I7|E2_MEDNUME|C|6|0|Num. Medição|Num. Medição|`@!` ||||N|A|R|||
I8|E2_MDDESC|N|15|2|Desconto Ctr|Desconto de Contrato|`@E 999,999,999.99` ||0||N|A|R|||
I9|E2_MDMULT|N|15|2|Multa Ctr|Multa de Contrato|`@E 999,999,999.99` ||0||N|A|R|||
J0|E2_BASEIRF|N|16|2|Base IRRF|Base IRRF|`@E 9,999,999,999,999.99` |`positivo() .and. fa050nat2()` |||N|A|R||`If(FindFunction('F050BSIMP'),F050BSIMP(1,1),.f.)` |
J1|E2_BASECOF|N|16|2|Base Cof|Base Cofins ref. titulo|`@E 9,999,999,999,999.99` |`positivo() .and. fa050nat2()` |||N|V|R||`If(FindFunction('F050BSIMP'),F050BSIMP(1,3),.f.)` |
J2|E2_CLVL|C|9|0|Classe Valor|Classe de Valor|`@!` |`(Vazio() .OR. Ctb105Clvl())` ||CTH|N|A|R||`CtbInUse()` |
J3|E2_CCUSTO|C|9|0|C. de Custo|Centro de Custo|`@!` |`Vazio() .or. CTB105CC()` ||CTT|N|A|R|||
J4|E2_CIDE|N|14|2|Cide|Valor do CIDE|`@E 99,999,999,999.99` |`Positivo() .And. FA050Cide()` ||||A|R||`M->E2_MULTNAT != '1'` |
J5|E2_CODAPRO|C|6|0|Cód. Aprov.|Código do Aprovador|`@!` |`Vazio() .Or. IIF(FindFunction("FA050VldAp"),FA050VldAp(M->E2_CODAPRO,M->E2_MOEDA),.T.)` |IIF(FindFunction("FA050Aprov") .AND. Inclui,FA050Aprov(M->E2_MOEDA),"")|FRP|S|||||
J6|E2_FAMAD|N|16|2|Vl.FAMAD|Valor do Famad|`@E 9,999,999,999,999.99` ||||N|A|R|||
J7|E2_FATFOR|C|6|0|Forn. Fatura|Fornecedor Fatura|`@!` ||||N|A|R|||
J8|E2_FATLOJ|C|2|0|Loja For Fat|Loja Fornecedor Fatura|`@!` ||||N|A|R|||
J9|E2_DIACTB|C|2|0|Cod. Diario|Cod. Diario da Contabilid|`@!` |`VldCodSeq()` |CtbRDia()|CVL|S||||`CtbWDia()` |
K0|E2_DATAAGE|D|8|0|Data Agend.|Data de Agendamento|||M->E2_VENCREA||N|A|R|||
K1|E2_NFELETR|C|20|0|NF Eletr.|Nota Fiscal Eletrônica|`@!` ||||N|A|R|||
K2|E2_NODIA|C|10|0|Seq. Diario|Seq. Diario Contabilidade|`@!` ||||S|V||||
K3|E2_PARCFAM|C|2|0|Parc.FAMAD|Parcela do tributo Famad|`@!` ||||N|A|R|||
K4|E2_PARCFMP|C|2|0|Parc.FUMIPEQ|Parcela Tributo Fumipeq|`@!` ||||N|A|R|||
K5|E2_PARCAGL|C|2|0|Parc.Aglut.|Parcelea aglutinadora|`@!` |||||||||
K6|E2_PRINSS|N|14|2|Prov INSS|Provisao de  - INSS|`@E 99,999,999,999.99` |||||A|R|||
K7|E2_PRETINS|C|1|0|Pend.Rt.INSS|Pendente Retenção - INSS||||||V||||
K8|E2_RETCNTR|N|15|2|Retencao Ctr|Retencao de Contrato|`@E 999,999,999.99` ||0||N|A|R|||
K9|E2_STATLIB|C|2|0|Status|Status de Aprovação|`@!` ||"01"||N|||||
L0|E2_RETINS|C|4|0|Ret. INSS|Código de Retenção INSS|`@!` |`If ( Empty(M->E2_RETINS),.T.,ExistCPO("SX5","QM"+M->E2_RETINS))` ||QM|N|||||
L1|E2_TPESOC|C|1|0|Tp de serv|Classif tp serviço||||DZ||A|R|||
L2|E2_TEMDOCS|C|1|0|Possui Docs|Possui documentos|`@!` |`Pertence("1|2|")` |"2"||S|A|R|1=Sim;2=Nao||
L3|E2_VRETINS|N|14|2|Vlr Ret INSS|Valor Retido INSS|`@E 99,999,999,999.99` ||||N|V||||
L4|E2_BASEINS|N|16|2|Base INSS|Base INSS|`@E 9,999,999,999,999.99` |`positivo() .and. fa050nat2()` |||N|A|R||`If(FindFunction('F050BSIMP'),F050BSIMP(1,5),.f.)` |
L5|E2_BTRISS|N|14|2|ISS Bitribut|Bitributação do ISS CPOM|`@E 99,999,999,999.99` |`Positivo() .and. IIF(M->E2_TIPO="PR" .and. M->E2_ISSBTR > 0,.F.,.T.)` |||N|A|R||`M->E2_MULTNAT != "1"` |
L6|E2_CODINS|C|4|0|Cod Ret INSS|Cod Retenção INSS||||38||||||
L7|E2_CNO|C|6|0|Cod CNO|Codigo CNO||`Vazio() .Or. ExistCpo('SON')` ||SON||A|R|||
L8|E2_CNPJRET|C|14|0|CNPJ Ret.|CNPJ do retentor|`@!` ||||N|||||
L9|E2_CODOPE|C|2|0|Cod. Operad.|Codigo Operadora de Frete|`@!` |`Vazio().OR.TmsValField('M->E2_CODOPE',.T.,'E2_NOMOPE')` ||DEG|N|A|R|||
M0|E2_CODRCOF|C|4|0|Cod.Ret Cof|Cod. Ret Cofins||||37||||||
M1|E2_CODRCSL|C|4|0|Cod.Ret CSL|Codigo Ret. CSL||||37||||||
M2|E2_CODRPIS|C|4|0|Cod.Ret.PIS|Cod. de Retencao PIS||||37||||||
M3|E2_CODSERV|C|9|0|Cod.Serv.ISS|Codigo de Servico do ISS|`@9` |`ExistCpo("SX5","60"+AllTrim(M->E2_CODSERV)) .and. Fa050Nat2()` ||60|N|A|R|||
M4|E2_DTBORDE|D|8|0|Dt. Bordero|Data do bordero|||||N|A|R|||
M5|E2_FABOV|N|14|2|Vlr.FABOV|Valor do tributo FABOV|`@E 99,999,999,999.99` |||||||||
M6|E2_FACS|N|14|2|Vlr.FACS|Valor do tributo FACS|`@E 99,999,999,999.99` |||||||||
M7|E2_MSIDENT|C|10|0|Ident.Reg.|Ident.Reg.|||||N|V|R|||
M8|E2_IDDARF|C|20|0|ID DARF|Identificação DARF|`@!` ||||S|||||
M9|E2_AGLIMP|C|9|0|Agl.Impostos|Aglutinacao de Impostos|`@!` ||||N|A||||
N0|E2_TIPOLIQ|C|3|0|Tipo Liquida|Tipo gerado p/Liquidação|`@!` ||||N|||||
N1|E2_TPDESC|C|1|0|Desc. F100|Desconto F100|`@!` |`Pertence("CI")` |'C'|||||||
N2|E2_VRETBIS|N|14|2|Vlr. Ret ISB|Vlr. Retenção ISS Bitrib.|`@E 99,999,999,999.99` |||||V|R|||
N3|E2_PRISS|N|14|2|Prov ISS|Provisao de  - ISS|`@E 99,999,999,999.99` ||||N|A|R|||
N4|E2_PARCCID|C|2|0|Parc. CIDE|Parcela do imposto|`@!` |||||A|R|||
N5|E2_PARCFAB|C|2|0|Parc.FABOV|Parcela do tributo FABOV|`@!` |||||||||
N6|E2_PARCFAC|C|2|0|Parc.FACS|Parcela do tributo FACS|`@!` |||||||||
N7|E2_PARIMP1|C|2|0|Parc.Imp.01|Parcela Imposto 01|`@!` ||||N|A|R|||
N8|E2_PARIMP2|C|2|0|Parc.Imp.02|Parcela Imposto 02|`@!` ||||N|A|R|||
N9|E2_PARIMP3|C|2|0|Parc.Imp.03|Parcela Imposto 03|`@!` ||||N|A|R|||
O0|E2_PARIMP4|C|2|0|Parc.Imp.05|Parcela Imposto 05|`@!` ||||N|A|R|||
O1|E2_PARIMP5|C|2|0|Parc.Imp.05|Parcela Imposto 05|`@!` ||||N|A|R|||
O2|E2_NUMSOL|C|6|0|No. Solic.|No. Solicitacäo de transf|`@!` ||||N|V|R|||
O3|E2_NOMOPE|C|30|0|Nome Operad.|Nome da Operadora de Fret|`@!` ||If(!Inclui,TMSValField("SE2->E2_CODOPE",.F.,"E2_NOMOPE"),"")||N|V|V|||


## SIX - Índices da tabela

ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|E2_FILIAL+E2_PREFIXO+E2_NUM+E2_PARCELA+E2_TIPO+E2_FORNECE+E2_LOJA|Prefixo + No. Titulo + Parcela + Tipo + Fornecedor + Loja|XXX+XXX+XXX+05+SA2||S|
2|E2_FILIAL+E2_NATUREZ+E2_NOMFOR+E2_PREFIXO+E2_NUM+E2_PARCELA+E2_TIPO+E2_FORNECE|Natureza + Nome Fornece + Prefixo + No. Titulo + Parcela + Tipo + Forn|SED+XXX+XXX+XXX+XXX+05+SA2||S|
3|E2_FILIAL+DTOS(E2_VENCREA)+E2_NOMFOR+E2_PREFIXO+E2_NUM+E2_PARCELA+E2_TIPO+E2_FILORIG|Vencto Real + Nome Fornece + Prefixo + No. Titulo + Parcela + Tipo + F|XXX+XXX+XXX+XXX+XXX+05||S|
4|E2_FILIAL+E2_PORTADO+E2_NOMFOR+E2_PREFIXO+E2_NUM+E2_PARCELA+E2_TIPO+E2_FORNECE|Portador + Nome Fornece + Prefixo + No. Titulo + Parcela + Tipo + Forn|BCO+XXX+XXX+XXX+XXX+05+SA2||S|
5|E2_FILIAL+DTOS(E2_EMISSAO)+E2_NOMFOR+E2_PREFIXO+E2_NUM+E2_PARCELA+E2_TIPO|DT Emissao + Nome Fornece + Prefixo + No. Titulo + Parcela + Tipo|XXX+XXX+XXX+XXX+XXX+05||S|
6|E2_FILIAL+E2_FORNECE+E2_LOJA+E2_PREFIXO+E2_NUM+E2_PARCELA+E2_TIPO|Fornecedor + Loja + Prefixo + No. Titulo + Parcela + Tipo|SA2+XXX+XXX+XXX+XXX+05||S|
7|E2_FILIAL+DTOS(E2_EMIS1)+E2_NATUREZ|DT Contab. + Natureza|XXX+SED||S|
8|E2_FILIAL+E2_ORDPAGO|Ordem Pagto|||S|
9|E2_FILIAL+E2_FORNECE+E2_LOJA+E2_FATPREF+E2_FATURA|Fornecedor + Loja + Pref. Fatura + Num Fatura|SA2||S|
A|E2_FILIAL+E2_FORNECE+E2_LOJA+E2_ANOBASE+E2_MESBASE+E2_PLOPELT+E2_PLLOTE|Fornecedor + Loja + Ano Base + Mes Base + Operadora Lt + Lote PLS|||S|
B|E2_FILIAL+E2_IDCNAB|Id. Cnab|||S|
C|E2_FILIAL+E2_PLOPELT+E2_PLLOTE+E2_NOMFOR|Operadora Lt + Lote PLS + Nome Fornece|||S|
D|E2_IDCNAB|Id. Cnab|||S|
E|E2_FILIAL+E2_NODIA|Seq. Diario|||S|
F|E2_FILIAL+E2_NUMBOR|Num Bordero|||S|
G|E2_FILIAL+E2_ARQRAT|Arq Rateio|||S|
H|E2_FILIAL+E2_TITPAI|Titulo Pai|||S|


