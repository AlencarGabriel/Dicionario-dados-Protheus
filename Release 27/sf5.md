# SF5 - Tipos de Movimentação
## SX3 - Campos da tabela

X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|F5_FILIAL|C|2|0|Filial|Filial do Sistema|||||N|||||
02|F5_CODIGO|C|3|0|Codigo TM|Codigo da Movimentacao|`@9` |`ExistChav("SF5").And.A230Tipo() .AND. Freeforuse("SF5") .And. EstVldStr()` |||S|||||
03|F5_TIPO|C|1|0|Tipo de TM|Tipo de Tipo de Movimento|`!` |`Pertence("DPR").And.A230Tipo()` |||S|||P=Producao;R=Requisicao;D=Devolucao||
04|F5_TEXTO|C|20|0|Descricao|Descricao da Movimentacao|`@!` |`Texto()` |||S|||||
05|F5_APROPR|C|1|0|Aprop.Indir|Apropria indireto diretam|`!` |`pertence("SN")` |||S|||S=Sim;N=Nao||
06|F5_ATUEMP|C|1|0|Atu.Empenho|Atualiza o empenho|`!` |`pertence("SN")` |||N|||S=Sim;N=Nao||
07|F5_TRANMOD|C|1|0|Transf.MOD.|Transfere somente a MOD ?|`!` |`pertence("SN")` |||N|||S=Sim;N=Nao||
08|F5_VAL|C|1|0|Valorizado|Movimento Valorizado|`@!` |`pertence("SN")` |"N"||N|A|R|S=Sim;N=Nao|`M->F5_GERAATF == '2'` |
09|F5_ENVCQPR|C|1|0|Envia p/CQ|Envia produção para C.Q.?|`@!` |`pertence("SN")` |"N"||N|||S=Sim;N=Nao||
10|F5_LIBPVPR|C|1|0|Libera PV|Libera PV amarrado a OP ?|`@!` |`pertence("SN")` |"N"||N|||S=Sim;N=Nao||
11|F5_QTDZERO|C|1|0|Qtd Zero|Qtd zerada no mov. valor?|`@9` |`Pertence("12") .And. If(M->F5_VAL$" N".And.&(ReadVar())=="1",(Help(" ",1,"QTD_ZERO"),.F.),.T.)` |"2"||S|||1=Sim;2=Nao||
12|F5_COPSIMP|C|7|0|Cod Op. SIMP|Codigo da Oper. SIMP|`9999999` |||D3C|S|A|R|||
13|F5_MOVTANQ|C|2|0|T.Mov.Tanque|Tipo de Mov. Tanque|`@!` ||||N|A|R|AP=Apuracao;BO=Fat_posterior;DE=Descarga;EQ=Equalizacao;PR=Provisorio;TR=Transferencia;GC=Producao automatica||
14|F5_AGREGCU|C|1|0|Custeia OP|Custeia OP com prd contr|`@!` |`Pertence("12 ")` |"1"||S|A|R|1=Sim;2=Nao;||
15|F5_CUSTATF|C|1|0|Cust Med Ati|Consid.Custo Medio Ativo|`@!` |`Pertence('12')` |"2"||N|A|R|1=Sim;2=Nao|`M->F5_GERAATF == '1'` |
16|F5_GERAATF|C|1|0|Gera Ativo?|Gera Ativo?||`Pertence('12')` |"2"||N|A|R|1=Sim;2=Não|`M->F5_VAL=='N'` |
17|F5_CODLAN|C|6|0|Cod.Cat83|Código Lcto Cat83|`@!` |`Vazio() .Or. ExistCpo('CDZ')` ||CDZ|S|A|R|||
18|F5_TEATF|C|3|0|Tipo Entrada|Tipo de Entrada da Nota|`@9` |`ExistCpo('SF4') .And.MaAvalTes('E',M->F5_TEATF) .And. A230VldTES()` ||SF4|N|A|R|||


## SIX - Índices da tabela

ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|F5_FILIAL+F5_CODIGO|Codigo TM|||S|
2|F5_FILIAL+F5_MOVTANQ+F5_TIPO|T.Mov.Tanque + Tipo de TM|||S|
3|F5_FILIAL+F5_COPSIMP|Cod Op. SIMP|||S|


