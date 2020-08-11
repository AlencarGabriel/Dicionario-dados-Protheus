# SE1 - Contas a Receber
## SX3 - Campos da tabela

X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|E1_FILIAL|C|2|0|Filial|Filial do Sistema|||"1"||N|||||
02|E1_PREFIXO|C|3|0|Prefixo|Prefixo do titulo|`@!` |`FA040Num()` |||S|||||
03|E1_NUM|C|9|0|No. Titulo|Numero do Titulo|`@!` |`FA040Num() .AND. FREEFORUSE("SE1",M->E1_NUM)` |||S|||||
04|E1_PARCELA|C|2|0|Parcela|Parcela do Titulo|`@!` |`F040VERPAR()` |||S|||||
05|E1_TIPO|C|3|0|Tipo|Tipo do titulo|`@!` |`FA040Tipo() .And. FA040Num() .And. FA040Natur()` ||05|S|||||
06|E1_NATUREZ|C|10|0|Natureza|Codigo da natureza|`@!` |`FA040Natur().and.FinVldNat( .F., M->E1_NATUREZ, 1 )` ||SED|S|||||
07|E1_PORTADO|C|3|0|Portador|Codigo do portador|`@!` |`existcpo("SA6")` ||BCO|S|||||
08|E1_AGEDEP|C|5|0|Depositaria|Agencia Depositaria|`@!` |`existcpo("SA6",M->E1_PORTADO+M->E1_AGEDEP)` |||N|||||
09|E1_CLIENTE|C|6|0|Cliente|Codigo do Cliente|`@!` |`existcpo("SA1",M->E1_CLIENTE,,,,.F.) .and. fa040Num() .And. FA040Natur()` ||SA1|S|||||
10|E1_LOJA|C|2|0|Loja|Loja do Cliente|`@!` |`existcpo("SA1",M->E1_CLIENTE+M->E1_LOJA) .And. Fa040Num() .And. FA040Natur()` |||S|||||
11|E1_NOMCLI|C|20|0|Nome Cliente|Nome Reduzido do Cliente|`@!` ||||N|V||||
12|E1_EMISSAO|D|8|0|DT Emissao|Data de Emissao do Titulo||`iif(empty(m->e1_vencto),.T.,m->e1_emissao <= m->e1_vencto) .and. F040VLDSBPR()` |ddatabase||S|||||
13|E1_VENCTO|D|8|0|Vencimento|Vencimento do Titulo||`FA040Venc()` |||S|||||
14|E1_VENCREA|D|8|0|Vencto real|Vencimento real do Titulo||`m->e1_vencrea>=m->e1_vencto .AND. F040VCREA()` |||S|||||
15|E1_VALOR|N|16|2|Vlr.Titulo|Valor do Titulo|`@E 9,999,999,999,999.99` |`positivo().and.naovazio().and.fa040natur().and.fa040valor()` |||S|||||
16|E1_BASEIRF|N|16|2|Base Imposto|Base Imposto|`@E 9,999,999,999,999.99` |`positivo() .and. fa040natur()` |||N|A|R||`If(FindFunction('F040BSIMP'),F040BSIMP(),.f.)` |
17|E1_IRRF|N|14|2|IRRF|Valor do IRRF|`@E 99,999,999,999.99` |`positivo().and.m->e1_irrf<m->e1_valor.and.IIF(m->e1_tipo="PR".and.m->e1_irrf > 0,.F.,.T.) .and. fa040valor()` |||S||||`M->E1_MULTNAT != "1"` |
18|E1_ISS|N|14|2|ISS|Valor do ISS|`@E 99,999,999,999.99` |`positivo() .and. m->e1_iss  < m->e1_valor .and. IIF(m->e1_tipo="PR" .and. m->e1_iss > 0,.F.,.T.) .and. fa040valor()` |||S||||`M->E1_MULTNAT != "1"` |
19|E1_NUMBCO|C|15|0|Nº no Banco|No. do Titulo no Banco|`@!` ||||N|||||
20|E1_INDICE|C|3|0|Reajuste|Cod da Tabela de Reajuste|`@!` ||||N|||||
21|E1_BAIXA|D|8|0|DT Baixa|Data de Baixa do Titulo|||dDataBase||N|||||
22|E1_NUMBOR|C|6|0|Num. Bordero|Numero do Bordero|`@!` ||||N|||||
23|E1_DATABOR|D|8|0|DT Bordero|Data do Bordero|||||N|||||
24|E1_EMIS1|D|8|0|DT Contab.|Data de Contabilizacao|||||N|||||
25|E1_HIST|C|40|0|Historico|Historico do Título|`@!` ||||S|||||
26|E1_LA|C|1|0|Ident. Lanc.|Identificador de LA|`@!` ||||N|||||
27|E1_LOTE|C|4|0|Lote Contabl|Lote Contabil|`@!` ||||N|||||
28|E1_MOTIVO|C|20|0|Motivo|Motivo do nao pagamento|`@!` ||||N|||||
29|E1_MOVIMEN|D|8|0|Ult.Moviment|Data da ultima movimentac|||||N|||||
30|E1_OP|C|14|0|Ord Producao|Ordem de producao|`@9` |`vazio().or.existcpo("SC2")` ||SC2|N|||||
31|E1_SITUACA|C|1|0|Situacao|Situacao do titulo||||FRV|N|||||
32|E1_CONTRAT|C|15|0|Contrato|Contrato com banco|`@S3` ||||N|||||
33|E1_SALDO|N|16|2|Saldo|Saldo a Receber|`@E 9,999,999,999,999.99` ||||N|A|R|||
34|E1_SUPERVI|C|6|0|Supervisor|Codigo do Supervisor|`@!` |`existcpo("SA3")` ||SA3|N|||||
35|E1_VEND1|C|6|0|Vendedor 1|Codigo do Vendedor 1|`@!` |`vazio() .or. existcpo("SA3")` ||SA3|N|||||
36|E1_VEND2|C|6|0|Vendedor 2|Codigo do Vendedor 2|`@!` |`vazio() .or. existcpo("SA3")` ||SA3|N|||||
37|E1_VEND3|C|6|0|Vendedor 3|Codigo do Vendedor 3|`@!` |`vazio() .or. existcpo("SA3")` ||SA3|N|||||
38|E1_VEND4|C|6|0|Vendedor 4|Codigo do Vendedor 4|`@!` |`vazio() .or. existcpo("SA3")` ||SA3|N|||||
39|E1_VEND5|C|6|0|Vendedor 5|Codigo do Vendedor 5|`@!` |`vazio() .or. existcpo("SA3")` ||SA3|N|||||
40|E1_COMIS1|N|6|2|% Comissao 1|% da Comissao 1|`@E 999.99` |`positivo() .and. FA040Comis()` |||N|||||
41|E1_COMIS2|N|6|2|% Comissao 2|% da Comissao 2|`@E 999.99` |`positivo() .and. FA040Comis()` |||N|||||
42|E1_COMIS3|N|6|2|% Comissao 3|% da Comissao 3|`@E 999.99` |`positivo() .and. FA040Comis()` |||N|||||
43|E1_COMIS4|N|6|2|% Comissao 4|% da Comissao 4|`@E 999.99` |`positivo() .and. FA040Comis()` |||N|||||
44|E1_DESCONT|N|16|2|Desconto|Desconto concedido|`@E 9,999,999,999,999.99` ||||N|||||
45|E1_COMIS5|N|6|2|% Comissao 5|% da Comissao 5|`@E 999.99` |`positivo() .and. FA040Comis()` |||N|||||
46|E1_MULTA|N|16|2|Multa|Valor da Multa|`@E 9,999,999,999,999.99` ||||N|||||
47|E1_JUROS|N|16|2|Juros|Valor do Juros|`@E 9,999,999,999,999.99` ||||N|||||
48|E1_CORREC|N|16|2|Correcao|Valor da Correcao|`@E 9,999,999,999,999.99` ||||N|||||
49|E1_VALLIQ|N|16|2|Vlr.Liq Baix|Valor Liquido da Baixa|`@E 9,999,999,999,999.99` ||||N|||||
50|E1_VENCORI|D|8|0|Vencto Orig|Vencimento Original|||||N|||||
51|E1_CONTA|C|10|0|Num da Conta|Numero da Conta Corrente|`@!` |`existcpo("SA6",m->e1_portado+m->e1_agedep+m->e1_conta)` |||N|||||
52|E1_VALJUR|N|14|2|Taxa Perman.|Taxa Permanencia Diaria|`@E 99,999,999,999.99` |`positivo() .and. m->e1_valjur < m->e1_valor` |||S|||||
53|E1_PORCJUR|N|5|2|Porc Juros|Porcentual Juros Diario|`@E 99.99` ||||S|||||
54|E1_MOEDA|N|2|0|Moeda|Moeda do Titulo|`99` |`Fa040moed().and.fa040Irf().And.FA040VALOR()` |1||S|||||
55|E1_BASCOM1|N|16|2|Base Comis 1|Base da Comis. do Vend. 1|`@E 9,999,999,999,999.99` ||||N|||||
56|E1_BASCOM2|N|16|2|Base Comis 2|Base da Comis. do Vend. 2|`@E 9,999,999,999,999.99` ||||N|||||
57|E1_BASCOM3|N|16|2|Base Comis 3|Base da Comis. do Vend. 3|`@E 9,999,999,999,999.99` ||||N|||||
58|E1_BASCOM4|N|16|2|Base Comis 4|Base da Comis. do Vend. 4|`@E 9,999,999,999,999.99` ||||N|||||
59|E1_BASCOM5|N|16|2|Base Comis 5|Base da Comis. do Vend. 5|`@E 9,999,999,999,999.99` ||||N|||||
60|E1_FATPREF|C|3|0|Pref. Fatura|Prefixo da Fatura gerada|`@!` ||||N|||||
61|E1_FATURA|C|9|0|Fatura|Numero da Fatura|`@!` ||||N|||||
62|E1_OK|C|2|0|Iden.Selecao|Identificador de Selecao|||||N|||||
63|E1_PROJETO|C|6|0|Projeto|Codigo do Projeto||`vazio() .or. ExistCPO("SX5","52"+M->E1_PROJETO)` ||52|N|||||
64|E1_CLASCON|C|5|0|Classific.|Classificacao||`vazio() .or. ExistCPO("SX5","51"+M->E1_CLASCON)` ||51|N|||||
65|E1_VALCOM1|N|16|2|Vlr. comis.1|Valor comissao vend. 1|`@E 9,999,999,999,999.99` |||||V||||
66|E1_VALCOM2|N|16|2|Vlr. comis.2|Valor comissao vend. 2|`@E 9,999,999,999,999.99` |||||V||||
67|E1_VALCOM3|N|16|2|Vlr. comis.3|Valor comissao vend. 3|`@E 9,999,999,999,999.99` |||||V||||
68|E1_VALCOM4|N|16|2|Vlr. comis.4|Valor comissao vend. 4|`@E 9,999,999,999,999.99` |||||V||||
69|E1_VALCOM5|N|16|2|Vlr. comis.5|Valor comissao vend. 5|`@E 9,999,999,999,999.99` |||||V||||
70|E1_OCORREN|C|2|0|Cod Ocorrenc|Codigo Ocorrencia CNAB|`@!` ||||N|||||
71|E1_INSTR1|C|2|0|Inst.Primar.|Instrucao primaria CNAB|`@!` ||||N|||||
72|E1_INSTR2|C|2|0|Instr.Secund|Instrucao secundaria CNAB|`@!` ||||N|||||
73|E1_PEDIDO|C|6|0|No. Pedido|Numero do Pedido|`@!` ||||N|||||
74|E1_DTVARIA|D|8|0|Dt UIt.Var.|Data da ultima variacao||||||||||
75|E1_VARURV|N|16|2|Vlr.Variacao|Valor da Variacao Apurada|`@E 9,999,999,999,999.99` |||||||||
76|E1_VLCRUZ|N|16|2|Vlr R$|Valor na moeda nacional|`@E 9,999,999,999,999.99` |||||||||
77|E1_DTFATUR|D|8|0|Data Faturam|Data Faturamento|||||N|||||
78|E1_NUMNOTA|C|9|0|Nota Fiscal|Numero da Nota Fiscal|`@!` ||||N|||||
79|E1_SERIE|C|3|0|Serie|Serie da Nota Fiscal|`!!!` ||||N|||||
80|E1_STATUS|C|1|0|Status|Status|`!` ||||N|||||
81|E1_ORIGEM|C|8|0|Origem|Origem do Título|||||N|||||
82|E1_IDENTEE|C|6|0|Ident CEC|Ident da Comp entre Cart|`@!` ||||N|||||
83|E1_NUMCART|C|19|0|Num do Carta|N·mero do Cartão|`@!` ||||N|V||||
84|E1_FLUXO|C|1|0|Fluxo Caixa|Fluxo de Caixa|`@!` |`pertence("SN")` |"S"|||||S=Sim;N=Nao||
85|E1_DESCFIN|N|5|2|Desc Financ.|Desconto Financeiro|`@E 99.99` ||||S|||||
86|E1_DIADESC|N|2|0|Dias p/ Desc|Dias para Desconto|`99` ||||S|||||
87|E1_TIPODES|C|1|0|Tipo Descont|Tipo do Desconto|||"1"|||||1=Fixo;2=Proporcional||
88|E1_CARTAO|C|16|0|Nro. Cartao|Nro. Cartao de Credito|`9999999999999999` ||||N|||||
89|E1_CARTVAL|D|8|0|Validade|Data de Validade do CC|||||N|||||
90|E1_CARTAUT|C|6|0|Autorização|Autorização do CC|`@!` ||||N|||||
91|E1_ADM|C|3|0|Administ.|Adm. de Cartao de Credito||||||A||||
92|E1_VLRREAL|N|16|2|Valor Real|Valor Real do Titulo|`@E 9,999,999,999,999.99` ||||N|||||
93|E1_TRANSF|C|15|0|Doc.Transf.|Numero do docto. transf.|`@!` ||||S|||||
94|E1_BCOCHQ|C|3|0|Bco. Cheque|Banco Cheque Liquidacao|`@!` ||||N|||||
95|E1_AGECHQ|C|5|0|Agenc.Cheque|Agencia Cheque Liquidacao|`@!` ||||N|||||
96|E1_CTACHQ|C|10|0|Conta Cheque|Conta Cheque Liquidacao|`@!` ||||N|||||
97|E1_NUMLIQ|C|6|0|N.Liquidacao|Numero da Liquidacao|`@!` |||||||||
98|E1_ORDPAGO|C|6|0|Ordem Pagto|Ordem de Pagamento|`@!` |||||||||
99|E1_RECIBO|C|6|0|No. Recibo|Numero de Recibo|`@!` ||||N|||||
A0|E1_INSS|N|14|2|INSS|Valor INSS|`@E 99,999,999,999.99` |`positivo() .and. m->e1_valor > m->e1_inss .and. IIF(m->e1_tipo == "PR " .and. m->e1_inss > 0 , .F. ,.T.) .and. fa040valor()` |||||||`M->E1_MULTNAT != "1"` |
A1|E1_FILORIG|C|2|0|Filial Orig|Filial de Origem||`VldFilOrig(M->E1_FILORIG)` |||N|||||
A2|E1_DTACRED|D|8|0|Data p/ Comp|Data para compensacäo|||||S|||||
A3|E1_TIPOFAT|C|3|0|Tipo Fatura|Tipo da Fatura|`@!` ||||N|||||
A4|E1_TIPOLIQ|C|3|0|Tipo Liquida|Tipo gerado p/Liquidacao|`@!` ||||N|||||
A5|E1_CSLL|N|14|2|CSLL|Valor CSLL|`@E 99,999,999,999.99` |`positivo() .and. m->e1_valor > m->e1_csll .and. IIF(m->e1_tipo == "PR " .and. m->e1_csll > 0 , .F. ,.T.) .and. fa040valor()` |||||||`M->E1_MULTNAT != "1"` |
A6|E1_COFINS|N|14|2|COFINS|Valor COFINS|`@E 99,999,999,999.99` |`positivo() .and. m->e1_valor > m->e1_cofins .and. IIF(m->e1_tipo == "PR " .and. m->e1_cofins > 0 , .F. ,.T.) .and. fa040valor()` |||||||`M->E1_MULTNAT != "1"` |
A7|E1_PIS|N|14|2|PIS/PASEP|Valor PIS|`@E 99,999,999,999.99` |`positivo() .and. m->e1_valor > m->e1_pis .and. IIF(m->e1_tipo == "PR " .and. m->e1_pis > 0 , .F. ,.T.) .and. fa040valor()` |||N||||`M->E1_MULTNAT != "1"` |
A8|E1_FLAGFAT|C|1|0|Flag Fatura|Flag para Faturas|`@!` ||||N|||||
A9|E1_MESBASE|C|2|0|Mes Base|Mes Base|`@!` ||||N|||||
B0|E1_ANOBASE|C|4|0|Ano Base|Ano Base|`@!` ||||N|||||
B1|E1_PLNUCOB|C|12|0|Num.Cobranca|Numero Cobranca|`@!` ||||N|||||
B2|E1_CODEMP|C|4|0|Empresa/Grup|Empresa/Grupo|`@!` ||||N|V||||
B3|E1_CODINT|C|4|0|Instituicao|Instituicao|`@!` ||||N|V||||
B4|E1_MATRIC|C|6|0|Matricula|Matricula|`@!` ||||N|V||||
B5|E1_TXMOEDA|N|11|4|Taxa moeda|Taxa da moeda|`@E 999999.9999` |`positivo() .AND. FA040VALOR()` |||N||||`WTxMoe(M->E1_MOEDA)` |
B6|E1_ACRESC|N|16|2|Acrescimo|Valor do Acrescimo|`@E 9,999,999,999,999.99` |`POSITIVO().AND. F040VLDSDAC() .AND.iiF(INCLUI,.T.,SE1->E1_SALDO>0) .AND. FINVLACDC('R')` |||S||||`!(MVRECANT == M->E1_TIPO )` |
B7|E1_SDACRES|N|16|2|Sld.Acresc.|Saldo do Acrescimo|`@E 9,999,999,999,999.99` ||||N|||||
B8|E1_DECRESC|N|16|2|Decrescimo|Valor do Decrescimo|`@E 9,999,999,999,999.99` |`(M->E1_DECRESC<M->E1_VALOR).AND.POSITIVO().AND.M->E1_ACRESC ==0.AND.iiF(INCLUI,.T.,SE1->E1_SALDO>0).OR.FINVLACDC('R')` |||S||||`!(MVRECANT == M->E1_TIPO )` |
B9|E1_SDDECRE|N|16|2|Sld.Decresc.|Saldo do Decrescimo|`@E 9,999,999,999,999.99` ||||N|||||
C0|E1_MULTNAT|C|1|0|Mult. Natur.|Multiplas naturezas p/Tit||`pertence("12") .and. Fa040MultNat()` |"2"||N|||1=Sim;2=Nao|`MV_MULNATR .AND. M->E1_DESDOBR == "2"` |
C1|E1_MSFIL|C|2|0|Filial Orig.|.|||||N|V||||
C2|E1_MSEMP|C|2|0|Empresa Orig|.|`@!` ||||N|V||||
C3|E1_PROJPMS|C|1|0|Rateio Proj.|Rateio de Projetos|||"2"||N|V||1=Sim;2=Nao||
C4|E1_DESDOBR|C|1|0|Desdobramen.|Desdobramento|`@!` |`IIF(M->E1_DESDOBR="1",F040DSDOBR(),.T.)` |'2'|||||1=Sim;2=Nao|`!lAltera` |
C5|E1_NRDOC|C|50|0|Nr.Documento|Numero do Documento|`@!` ||||N|||||
C6|E1_MODSPB|C|1|0|Mod. Recebto|Modalidade Rec.Previsto|`@!` |`Pertence("123") .and. SPBTIPO("SE1")` |"1"||S|||1=TED;2=CIP;3=COMP|`SpbInUse()` |
C7|E1_EMITCHQ|C|40|0|Emitente CHQ|Emitente do Cheque|`@!` |||||||||
C8|E1_IDCNAB|C|10|0|Id. Cnab|Identificador Cnab|`@!` ||||N|||||
C9|E1_PLCOEMP|C|12|0|Contr Empres|Contrato Empresa|`@!` |||||||||
D0|E1_PLTPCOE|C|1|0|Tp Cont Empr|Tipo Contrato Empresa|`@!` |||||||||
D1|E1_CODCOR|C|6|0|Cod Corretor|Codigo Corretor|`@!` |||||||||
D2|E1_PARCCSS|C|2|0|Parc.CSS|Parcela do Funrural|`@!` |||||||||
D3|E1_CODORCA|C|8|0|Cod. Orcam.|Codigo do Orcamento|||||S|||||
D4|E1_CODIMOV|C|12|0|Cod. Imovel|Codigo do Imovel||||N01||||||
D5|E1_FILDEB|C|2|0|Fil.Debito|Filial de Debito||||||||||
D6|E1_NUMRA|C|15|0|Numero RA|Numero da RA Aluno|`@!` ||||N|V||||
D7|E1_NUMSOL|C|6|0|No. Solic.|No. Solicitacäo de transf|||||S|V|R|||
D8|E1_INSCRIC|C|10|0|Inscric.P.S.|Inscric.Processo Seletivo|`@!` ||||N|||||
D9|E1_SERREC|C|3|0|Serie Recibo|Serie do Recibo|`!!!` |||RN|S|||||
E0|E1_DATAEDI|D|8|0|Data EDI|Data de Geracao do EDI||||||V|R|||
E1|E1_CODBAR|C|44|0|Codig.Barras|Codigo de Barras|`@!` ||||N|V||||
E2|E1_CODDIG|C|48|0|Codig.Digita|Codigo Digitado|`@!` ||||N|||||
E3|E1_CHQDEV|C|1|0|Chq Devolvid|Cheque devolvido|`@!` ||||N|||||
E4|E1_LIDESCF|D|8|0|Lim Desc Fin|Data Limite p/Desc Financ||`M->E1_LIDESCF >= M->E1_VENCREA` |||N|||||
E5|E1_VLBOLSA|N|15|2|Valor Bolsa|Valor da Bolsa|`@E 999,999,999,999.99` ||||N|||||
E6|E1_VLFIES|N|15|2|Bolsa Fies|Valor da Bolsa FIES|`@E 999,999,999,999.99` ||||N|||||
E7|E1_NUMCRD|C|10|0|Contr Financ|Numero Contrato Financiam|`@!` ||||N|||||
E8|E1_DEBITO|C|20|0|Conta Deb.|Conta Contabil a Debito|`@!` |`Vazio() .or. CTB105CTA()` ||CT1|N|A|R|||
E9|E1_CCD|C|9|0|C.Custo Deb.|C.Custo a Debito|`@!` |`Vazio() .or. CTB105CC()` ||CTT|N|A|R|||
F0|E1_ITEMD|C|9|0|Item Ctb.Deb|Item Contabil a Debito|`@!` |`Vazio() .or. CTB105ITEM()` ||CTD|N|A|R|||
F1|E1_CLVLDB|C|9|0|Cl.Vlr. Deb.|Classe de Valor a Debito|`@!` |`Vazio() .or. CTB105CLVL()` ||CTH|N|A|R|||
F2|E1_CREDIT|C|20|0|Conta Cred.|Conta Contabil a Credito|`@!` |`Vazio() .or. CTB105CTA()` ||CT1|N|A|R|||
F3|E1_CCC|C|9|0|C.Custo Cred|C.Custo a Credito|`@!` |`Vazio() .or. CTB105CC()` ||CTT|N|A|R|||
F4|E1_ITEMC|C|9|0|It.Ctb.Cred.|Item Contabil Credito|`@!` |`Vazio() .or. CTB105ITEM()` ||CTD|N|A|R|||
F5|E1_CLVLCR|C|9|0|Cl.Vlr. Cred|Classe de Valor a Credito|`@!` |`Vazio() .or. CTB105CLVL()` ||CTH|N|A|R|||
F6|E1_DESCON1|N|15|2|Desconto|Valor do Desconto 1a faix|`@E 999,999,999,999.99` ||||N|||||
F7|E1_DESCON2|N|15|2|Desconto|Valor do Desconto 2a faix|`@E 999,999,999,999.99` ||||N|||||
F8|E1_DTDESC3|D|8|0|Dat.Desconto|Data do Desconto 1a faixa|||||N|||||
F9|E1_DTDESC1|D|8|0|Dat.Desconto|Data do Desconto 2a faixa|||||N|||||
G0|E1_DTDESC2|D|8|0|Dat.Desconto|Data do Desconto 3a faixa|||||N|||||
G1|E1_VLMULTA|N|15|2|Valor Multa|Valor da Multa no Boleto|`@E 999,999,999,999.99` ||||N|||||
G2|E1_DESCON3|N|15|2|Desconto|Valor do Desconto 3a faix|`@E 999,999,999,999.99` ||||N|||||
G3|E1_MOTNEG|C|3|0|Motivo Negoc|Motivo da Negociacao|`@!` |||FU|N|||||
G4|E1_SABTPIS|N|14|2|Saldo Ab.Pis|Saldo a abater - PIS|`@E 99,999,999,999.99` |||||||||
G5|E1_SABTCOF|N|14|2|Saldo Ab.COF|Saldo Abater - COFINS|`@E 99,999,999,999.99` |||||||||
G6|E1_SABTCSL|N|14|2|Saldo Ab.CSL|Saldo a abater - CSLL|`@E 99,999,999,999.99` |||||||||
G7|E1_FORNISS|C|6|0|Forn.ISS|Fornecedor do ISS|`@!` |`ExistCpo("SA2",M->E1_FORNISS+"00")` ||SA2||||||
G8|E1_PARTOT|C|4|0|Parcela atua|Parcela atual|`@R99/99` ||||N|||||
G9|E1_SITFAT|C|1|0|Sit. Fatura|Situacäo da fatura||||||||1=Fatura näo impressa;2=Fatura impressa;3=Fatura cancelada||
H0|E1_BASEPIS|N|14|2|Base Pis|Base do Pis Ref. Titulo|`@E 99,999,999,999.99` ||||N|V|R|||
H1|E1_BASECOF|N|14|2|Base Cof|Base Cofins ref. titulo|`@E 99,999,999,999.99` ||||N|V|R|||
H2|E1_BASECSL|N|14|2|Base Csll|Base Csll ref. titulo|`@E 99,999,999,999.99` ||||N|V|R|||
H3|E1_VRETISS|N|14|2|Valor Rt.ISS|Valor Retido - ISS|`@E 99,999,999,999.99` |||||V||||
H4|E1_PARCIRF|C|2|0|Parcela IRRF|Parcela Titulo IRRF|`@!` ||||N|A|R|||
H5|E1_SCORGP|C|1|0|PisCof OrgP.|Apura Pis/Cofins Org.Publ|`@!` |`Pertence("12")` |"2"|||||1=Sim;2=Não||
H6|E1_FRETISS|C|1|0|Form Ret ISS|Forma de retenção do ISS|`@!` ||||N|A|R|1=Cons. Vlr. Min;2=Sempre Retém||
H7|E1_TXMDCOR|N|14|4|Tx Cor.Moeda|Tx. Moeda na Correcao M.|`@E 999,999,999.9999` |||||||||
H8|E1_SATBIRF|N|14|2|Saldo Ab.irf|Saldo a abater - IRRF|`@E 99,999,999,999.99` |||||||||
H9|E1_TIPREG|C|2|0|Tp. Registro|Tipo de Registro|`@!` |||||V||||
I0|E1_CONEMP|C|12|0|Contr. Empr.|Contrato Empresa|`@!` |||||||||
I1|E1_VERCON|C|3|0|Versão Contr|Versão do Contrato|`@!` |||||V|R|||
I2|E1_SUBCON|C|9|0|Sub-Contrato|Sub-Contrato|`@!` |||||||||
I3|E1_VERSUB|C|3|0|Versao Sub|Versao SubContrato|`@!` |||||V||||
I4|E1_PLLOTE|C|10|0|Lote PLS|Número do Lote do PLS|`@!` |||||||||
I5|E1_PLOPELT|C|4|0|Operadora Lt|Operadora Lote Pagamento|`@!` |||||V||||
I6|E1_CODRDA|C|6|0|Código RDA|Código da Rede de Atendim|`@!` |||||V||||
I7|E1_FORMREC|C|2|0|Forma Pagto|Código da Forma de Pagto|`@!` |`Vazio() .or. ExistCpo("BQL",M->BA3_TIPPAG,1)` ||||||||
I8|E1_BCOCLI|C|3|0|Banco Client|Banco do Cliente|`@!` |||||||||
I9|E1_AGECLI|C|5|0|Agencia Cli.|Agência do Cliente|`@!` |||||||||
J0|E1_CTACLI|C|10|0|Conta Cli.|Conta do Cliente|`@!` |||||||||
J1|E1_PARCFET|C|2|0|Parc.FETHAB|Parcela do Imposto FETHAB|`@!` |||||||||
J2|E1_FETHAB|N|14|2|Vlr.FETHAB|Valor do Imposto FETHAB|`@E 99,999,999,999.99` |||||||||
J3|E1_MDCRON|C|6|0|Num. Cronogr|Número do Cronograma|`@!` ||||N|V|R|||
J4|E1_MDCONTR|C|15|0|Num. Contrat|Num. Contrato|||||N|V|R|||
J5|E1_MEDNUME|C|6|0|Num. Medição|Número da Medição|`@!` ||||N|V|R|||
J6|E1_MDPLANI|C|6|0|Num. Planilh|Num. Planilha|`@!` ||||N|V|R|||
J7|E1_MDPARCE|C|2|0|Num. Parcela|Número da Parcela|`@!` ||||N|V|R|||
J8|E1_MDREVIS|C|3|0|Revisão|Revisão do Contrato|`@!` ||||N|V|R|||
J9|E1_NUMMOV|C|2|0|Movimento|Movimento do Dia|||||N|A|R|||
K0|E1_PREFORI|C|3|0|Pref Origem|Prefixo Origem|`@!` ||||N|A|R|||
K1|E1_IDMOV|C|10|0|Id.Mov.|Id. Movimento|`@!` |||||V|R|||
K2|E1_PARCIMA|C|2|0|Parc. IMA|Parcela do Imposto IMA|`@!` ||||N|A|R|||
K3|E1_IMA|N|14|2|Valor IMA|Valor do Imposto IMA|`@E 99,999,999,999.99` ||||N|A|R|||
K4|E1_BOLETO|C|1|0|Gera boleto|Gera boleto p/ o título|`@!` |`Vazio() .Or. Pertence("12")` |" "||S|A|R|1=Sim;2=Não||
K5|E1_NUMPRO|C|10|0|Proc. Refer.|Nro Proc. Referenciado|`@!` |`Vazio().Or.ExistCpo('CCF')` ||CCF|S|A|R|||
K6|E1_INDPRO|C|1|0|Tp. Processo|Tipo de Processo|`@!` |`Pertence(" 01239")` |||S|V|R|0=Sefaz;1=Justiça Federal;2=Justiça Estadual;3=Secex/SRF;9=Outros||
K7|E1_ITEMCTA|C|9|0|Item Contab.|Item Contabil|`@!` |`(Vazio().Or.Ctb105Item())` ||CTD|N|A|R||`CtbInUse()` |
K8|E1_JURFAT|C|50|0|Num Fat Jur|Numero Fatura Juridico||||||||||
K9|E1_MDBONI|N|15|2|Bonific Ctr|Bonificacao de Contrato|`@E 999,999,999,999.99` ||0||N|A|R|||
L0|E1_MDDESC|N|15|2|Desconto Ctr|Desconto de Contrato|`@E 999,999,999,999.99` ||0||N|A|R|||
L1|E1_MDMULT|N|15|2|Multa Ctr|Multa de Contrato|`@E 999,999,999,999.99` ||0||N|A|R|||
L2|E1_MULTDIA|N|9|2|Multa ao Dia|Multa ao Dia|||||N||R|||
L3|E1_NFELETR|C|20|0|NF Eletr|Nota Fiscal Eletrônica|`@!` ||||S|A|R|||
L4|E1_NODIA|C|10|0|Seq. Diario|Seq. Diario Contabilidade|`@!` ||||S|V||||
L5|E1_PARCFMP|C|1|0|Parc.FUMIPEQ|Parcela tributo Fumipeq|`@!` ||||N|A|R|||
L6|E1_PARCFAB|C|2|0|Parc.FABOV|Parcela do tributo FABOV|`@!` |||||||||
L7|E1_PARCFAC|C|2|0|Parc.FACS|Parcela do tributo FACS|`@!` |||||||||
L8|E1_PARCFAM|C|1|0|Parc.FAMAD|Parc.FAMAD|`@!` ||||N|A|R|||
L9|E1_PARTPDP|C|1|0|Par. TPDP|Par. TPDP|`@!` |||||||||
M0|E1_CCUSTO|C|9|0|C. de Custo|Centro de Custo|`@!` |`Vazio() .or. CTB105CC()` ||CTT|N|A|R|||
M1|E1_CDRETCS|C|4|0|Cod. Ret. CS|Código de Retenção CSLL|`@!` ||||N|A|R|||
M2|E1_CDRETIR|C|4|0|Cod. Ret. IR|Código de Retenção do IR|`@!` ||||N|A|R|||
M3|E1_CLVL|C|9|0|Classe Valor|Classe de Valor|`@!` |`(Vazio().Or.Ctb105Clvl())` ||CTH|N|A|R||`CtbInUse()` |
M4|E1_CODRET|C|4|0|Cod. Ret.PCC|Codigo Retencao do PCC|`@!` |`(Vazio().Or.ExistCpo('SX5','37'+M->E1_CODRET)).and.fa040natur().and.fa040valor()` ||37|S|||||
M5|E1_FABOV|N|14|2|Vlr.FABOV|"Valor do tributo FABOV|`@E 99,999,999,999.99` |||||||||
M6|E1_FACS|N|14|2|Vlr.FACS|Valor do tributo FACS|`@E 99,999,999,999.99` |||||||||
M7|E1_FAMAD|N|16|2|Vl.FAMAD|Valor do Famad|`@E 9,999,999,999,999.99` ||||N|A|R|||
M8|E1_FMPEQ|N|16|2|Vl.FUMIPEQ|Valor do tributo FUMIPEQ.|`@E 9,999,999,999,999.99` ||||N|A|R|||
M9|E1_DESCJUR|N|5|2|Desc.Juros|Desconto Juros|`@E 99.99` ||||N|A|R|||
N0|E1_DOCTEF|C|20|0|Num. NSU|Numero NSU-SITEF|`@!` ||||S|A|R|||
N1|E1_PRINSS|N|14|2|Prov INSS|Provisao de  - INSS|`@E 99,999,999,999.99` |||||V|R|||
N2|E1_RATFIN|C|1|0|Rateio Fin|Rateio Financeiro|`@!` |`pertence("12").And. If(M->E1_RATFIN="1",F641RatFin("FINA040"),.T.)` |"2"||N|A|R|1=Sim;2=Não||
N3|E1_RELATO|C|1|0|Env. Relato|Enviado no Relato|`@!` |`Pertence('12')` |"2"||N|V|R|1=Sim;2=Nao||
N4|E1_RETCNTR|N|15|2|Retencao Ctr|Retencao de Contrato|`@E 999,999,999,999.99` ||0||N|A|R|||
N5|E1_TITPAI|C|50|0|Titulo Pai|Titulo Originário Imposto|||||N|A|R|||
N6|E1_TPDESC|C|1|0|Desc. F100|Desconto F100|`@!` |`Pertence("CI")` |"C"|||||||
N7|E1_TPDP|N|14|2|Vlr. TPDP|Vlr. TPDP|`@E 99,999,999,999.99` |||||||||
N8|E1_VLMINIS|C|1|0|Vlr Min ISS|Aplica Vlr. Minimo ISS|`@!` |`Pertence(" 12")` |"1"||S|||||
N9|E1_BASEINS|N|16|2|Base INSS|Base de INSS|`@E 9,999,999,999,999.99` |`positivo() .and. fa040natur()` |||N|A|R||`If(FindFunction('F040BSIMP'),F040BSIMP(),.f.)` |
O0|E1_NUMCON|C|20|0|Nro.Contrato|Número do Contrato|`@!` |||||||||
O1|E1_NOPER|N|11|0|N. Trans|Num Trans Caixa|`@E 99,999,999,999` ||||N|V|R|||
O2|E1_NUMINSC|N|15|0|Num. Inscr.|Numero Inscricao|`@E 999,999,999,999,999` ||||||R|||
O3|E1_NSUTEF|C|12|0|NSU SITEF|Numero NSU SITEF|`@!` ||||S|A|R|||
O4|E1_PERLET|C|4|0|Per. Letivo|Período Letivo|`@!` ||||S|A|R|||
O5|E1_LTCXA|C|10|0|Lote Cxa|Lote do Caixa|`@!` ||||N|A|R|||
O6|E1_DIACTB|C|2|0|Cod. Diario|Cod. Diario Contabilidade|`@!` |`VldCodSeq()` |CtbRDia()|CVL|S|A|||`CtbWDia()` |
O7|E1_IDLAN|N|9|0|Nr. Lancto.|Nr. Lancamento na FLAN|`@E 999,999,999` ||||N||R|||
O8|E1_IDAPLIC|N|9|0|Matriz Aplic|Matriz Aplicada|`@E 999,999,999` ||||N||R|||
O9|E1_IDBOLET|N|9|0|Id.Boleto|Id. Boleto|`@E 999,999,999` ||||||R|||
P0|E1_CODSERV|C|9|0|Cod.Serv.ISS|Codigo de Servico do ISS|`@9` |`ExistCpo("SX5","60"+AllTrim(M->E1_CODSERV)) .and. Fa040Natur()` ||60|N|A|R|||
P1|E1_CODIRRF|C|4|0|Cod.Rec.IRRF|Código da Receita - IRRF|`@!` ||||S|A|R|||
P2|E1_CODISS|C|6|0|Cod.Aliq.ISS|Codigo Aliquota ISS|`@!` |`ExistCpo( 'FIM', M->E1_CODISS ).AND.fa040natur().and.fa040valor()` ||FIM|S|A|R|||
P3|E1_CTRBCO|C|50|0|Contr MCMV|Contrato Minha Casa Minha|`@!` ||||S|A|R|||
P4|E1_CONHTL|C|32|0|Conta Hotel|Número da Conta Hoteleira|`@!` ||||N|A|R|||
P5|E1_CNO|C|6|0|Cod CNO|Codigo CNO|`@!` |`Vazio() .Or. ExistCpo('SON')` ||SON|N|A|R|||
P6|E1_CHAVENF|C|12|0|Chave NF|Chave da Nota Fiscal|`@!` ||||N|A|R|||
P7|E1_BTRISS|N|14|2|ISS Bitribut|Bitributação do ISS CPOM|`@E 99,999,999,999.99` |`Positivo() .and. IIF(M->E1_TIPO="PR" .and. M->E1_ISSBTR > 0,.F.,.T.)` |||N|A|R||`M->E1_MULTNAT != "1"` |
P8|E1_VRETBIS|N|14|2|Vlr. Ret ISB|Vlr. Retenção ISS Bitrib.|`@E 99,999,999,999.99` |||||V|R|||
P9|E1_VRETIRF|N|14|2|Vlr.Rt.Irf|Valor Retencao Irrf|`@E 99,999,999,999.99` ||||N|||||
Q0|E1_VLBOLP|N|9|2|Bolsa Pontu.|Valor Bolsa Pontualidade|`@E 999,999.99` ||||N||R|||
Q1|E1_TURMA|C|20|0|Turma|Turma|||||N||R|||
Q2|E1_TCONHTL|C|1|0|Tipo Conta|Tipo da Conta - Hotelaria||`Pertence("1234")` |"3"|||A|R|1=Evento;2=Grupo;3=Individual;4=Avulsa||
Q3|E1_TPESOC|C|2|0|Tp serviço|Classif tipo de serviço|`@!` |||DZ|N|A|R|||
Q4|E1_SERVICO|C|10|0|Cod. Servico|Codigo do Servico|`@!` ||||N||R|||
Q5|E1_SDOC|C|3|0|Série Doc.|Série do Documento Fiscal|`!!!` ||||N|V|R|||
Q6|E1_SDOCREC|C|3|0|Série Recibo|Série do Recibo|`!!!` ||||N|V|R|||
Q7|E1_SEQBX|C|2|0|Seq. Baixa|Sequencia de Baixa|`@!` ||||N|A|R|||
Q8|E1_SABTIRF|N|14|2|Sld Abt Irrf|Saldo de Abatimento IRRF|`@E 99,999,999,999.99` |||||||||
Q9|E1_PRISS|N|14|2|Prov ISS|Provisao de  - ISS|`@E 99,999,999,999.99` |||||V|R|||
R0|E1_PROCEL|N|15|0|Proc. Sel.|Processo Seletivo|`@E 999,999,999,999,999` ||||||R|||
R1|E1_PRODUTO|C|15|0|Produto|Cod. Produto p/ Fatura|`@!` |`Vazio() .Or. ExistCpo('SB1')` ||SB1|S|||||
R2|E1_BASEISS|N|16|2|Base ISS|Base ISS|`@E 9,999,999,999,999.99` |`positivo() .and. fa040natur()` |||N|A|R||`If(FindFunction('F040BSIMP'),F040BSIMP(),.f.)` |
R3|E1_APLVLMN|C|1|0|Aplica Vlr.|Aplica Valor Minimo|`@!` |`pertence("12")` |"1"||||R|1=Sim;2=Nao||


## SIX - Índices da tabela

ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|E1_FILIAL+E1_PREFIXO+E1_NUM+E1_PARCELA+E1_TIPO|Prefixo + No. Titulo + Parcela + Tipo|XXX+XXX+XXX+05||S|
2|E1_FILIAL+E1_CLIENTE+E1_LOJA+E1_PREFIXO+E1_NUM+E1_PARCELA+E1_TIPO|Cliente + Loja + Prefixo + No. Titulo + Parcela + Tipo|SA1+XXX+XXX+XXX+XXX+05||S|
3|E1_FILIAL+E1_NATUREZ+E1_NOMCLI+E1_PREFIXO+E1_NUM+E1_TIPO|Natureza + Nome Cliente + Prefixo + No. Titulo + Tipo|SED+XXX+XXX+XXX+05||S|
4|E1_FILIAL+E1_PORTADO+E1_NOMCLI+E1_PREFIXO+E1_NUM+E1_TIPO|Portador + Nome Cliente + Prefixo + No. Titulo + Tipo|SA6+XXX+XXX+XXX+05||S|
5|E1_FILIAL+E1_NUMBOR+E1_NOMCLI+E1_PREFIXO+E1_NUM+E1_PARCELA+E1_TIPO|Num. Bordero + Nome Cliente + Prefixo + No. Titulo + Parcela + Tipo|XXX+XXX+XXX+XXX+XXX+05||S|
6|E1_FILIAL+DTOS(E1_EMISSAO)+E1_NOMCLI+E1_PREFIXO+E1_NUM+E1_PARCELA|DT Emissao + Nome Cliente + Prefixo + No. Titulo + Parcela|||S|
7|E1_FILIAL+DTOS(E1_VENCREA)+E1_NOMCLI+E1_PREFIXO+E1_NUM+E1_PARCELA|Vencto real + Nome Cliente + Prefixo + No. Titulo + Parcela|||S|
8|E1_FILIAL+E1_CLIENTE+E1_LOJA+E1_STATUS+DTOS(E1_VENCREA)|Cliente + Loja + Status + Vencto real|SA1||S|
9|E1_FILIAL+E1_NRDOC+E1_PREFIXO+E1_CLIENTE+E1_LOJA|Nr.Documento + Prefixo + Cliente + Loja|||S|
A|E1_FILIAL+E1_CLIENTE+E1_LOJA+E1_FATPREF+E1_FATURA|Cliente + Loja + Pref. Fatura + Fatura|SA1||S|
B|E1_FILIAL+DTOS(E1_EMISSAO)+E1_NATUREZ+E1_CLIENTE+E1_LOJA+E1_TIPO|DT Emissao + Natureza + Cliente + Loja + Tipo|XXX+SED||S|
C|E1_FILIAL+E1_NUMBOR+DTOS(E1_EMISSAO)|Num. Bordero + DT Emissao|||S|
D|E1_FILIAL+E1_ORDPAGO|Ordem Pagto|||S|
E|E1_FILIAL+E1_CODINT+E1_CODEMP+E1_MATRIC+E1_ANOBASE+E1_MESBASE|Instituicao + Empresa/Grup + Matricula + Ano Base + Mes Base|||S|
F|E1_FILIAL+E1_NUMLIQ|N.Liquidacao|XXX||S|
G|E1_FILIAL+E1_IDCNAB|Id. Cnab|||S|
H|E1_FILIAL+E1_CODIMOV|Cod. Imovel|||S|
I|E1_FILIAL+E1_NUMRA+DTOS(E1_VENCTO)+E1_PREFIXO|Numero RA + Vencimento + Prefixo|||S|
J|E1_IDCNAB|Id. Cnab|||S|
K|E1_FILIAL+E1_NODIA|Seq. Diario|||S|
L|E1_FILIAL+E1_DOCTEF|Num. NSU||IDXFINA01|S|
M|E1_FILIAL+E1_NFELETR|NF Eletr|||S|
N|E1_FILIAL+DTOS(E1_EMISSAO)+E1_NSUTEF|DT Emissao + NSU SITEF|||S|
O|E1_FILIAL+DTOS(E1_EMISSAO)+E1_DOCTEF|DT Emissao + Num. NSU|||S|
P|E1_FILIAL+E1_JURFAT|Num Fat Jur|||S|
Q|E1_FILIAL+E1_PORTADO+E1_AGEDEP+E1_CONTA+E1_BCOCHQ+E1_AGECHQ+E1_CTACHQ+E1_PREFIXO+E1_NUM|Portador + Depositaria + Num da Conta + Bco. Cheque + Agenc.Cheque + C|||S|
R|E1_FILIAL+DTOS(E1_EMISSAO)+E1_PARCELA+E1_NSUTEF+E1_TIPO+DTOS(E1_VENCREA)|DT Emissao + Parcela + NSU SITEF + Tipo + Vencto real|||S|
S|E1_FILIAL+E1_TITPAI|Titulo Pai|FILIAL + TITULO PAI|TITPAI|S|


