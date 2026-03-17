# Como fazer uma boa Research

![banner.png.png](Como%20fazer%20uma%20boa%20Research/banner.png.png)

# **Summary**

Tirando o nome **obvio**, esse blogpost não são dicas que vão te ajudar a “explorar” um bug ou te dar dicas de como encontrar bugs fodas, é obvio que voce precisa do conhecimento tecnico. Entretanto nesse blogpost irei detalhar a minha experiencia fazendo research, sem muito preparo. E como eu fiquei focado e mantive as esperanças mesmo quando tuda dava errado.

Recentemente decidi focar em entender não so nos fundamentos tecnicos, mas sim o “mindset” (desculpe pelo uso dessa palavra hehehehe) de quem faz pesquisa e é capaz de encontrar vulnerabilidades em softwares amplamente usados. E decidi ficar alguns meses estudando e aprimorando essa skill, desde de o auxilio de AI para como se manter focado numa pesquisa.

![researchmeme.png](Como%20fazer%20uma%20boa%20Research/researchmeme.png)

# O que é fazer Research afinal?

Em questão é necessario entender que fazer Research não é um processo linear é um processo lento e totalmente ortogonal, você pode voltar em uma **etapa** ir para **frente** desistir **voltar** outro dia. Para o fim de exemplificação olhe a imagem abaixo

![MAIS.png](Como%20fazer%20uma%20boa%20Research/MAIS.png)

Nem sempre voce ira encontrar o bug no seu primeiro dia, as vezes precisa de meses as vezes até anos. Mas claro, o importante é nao desistir e continuar focado!

# Escolhendo o Target!

Então vamos começar…. Obviamente voce precisa de um alvo para começar a fazer pesquisa, seja os mais dificeis como browser ou ate mesmo algo mais simples como um emulador de gameboy. Apenas pegue algo que voce gostaria de fazer pesquisa e comece.  **Mas afinal como saber se eu realmente quero fazer pesquisa nesse target?**

- Perguntas que voce deve fazer para si mesmo….
    - Eu gosto desse target?
    - Eu conheço esse target o suficiente?
    - Eu tenho motivação e disciplina para ficar meses nesse target?

Se pelo menos 2 dessas respostas forem **“SIM”,** você tem um bom target que voce pode olhar. Mas claro dependendo da dificuldade será muito mais trabalhoso… Mas claro nunca é **“impossivel”**

# Escolhendo uma attack-surface!

Imagine o seu target não como uma aplicação final, mas sim como um conjunto de varios sub componentes e essa é a parte (talvez) mais importante da pesquisa, pois caso voce escolha uma attack surface boa voce **anda uma casa**, uma ruim voce perde dias ou ate meses em um target **ruim (perdendo tempo).** Isso dai é um processo lento e demorado, não deve ser rapido. O que eu gosto de se fazer é mapear todas as attack surface boas, mas é importante avaliar todas suas opções antes de qualquer coisa, além do mais: uma boa attack surface é algo que cumpre esses requisitos:

- Pouco auditada
- Complexa
- Tem bastante código novo ou que mudou recentemente
- Lida com input do usuário de alguma forma (parsing, deserialização, etc)
- Tem historico de bugs anteriores (onde teve 1 bug provavelmente tem mais)

Pense assim: se um componente já foi auditado por 500 pessoas e teve 200 CVEs nos ultimos anos, **talvez** os bugs mais faceis já foram. Mas se voce achar um cantinho do código que ninguém olhou direito, que é complexo e que processa dados de fora… ai sim voce tem **ouro**.

# Entendendo o código

Beleza, voce ja escolheu seu target e sua attack surface. Agora vem a parte que muita gente pula (e não deveria): **entender o código de verdade**. Não estou falando de ler superficialmente e achar que entendeu. Estou falando de sentar, abrir o código fonte, e entender o **fluxo** do dado desde a entrada até onde ele é processado.

Eu sei que parece chato (e as vezes é hehehe), mas essa etapa é o que separa quem encontra bugs de quem fica só tentando. Algumas coisas que eu faço nessa etapa:

- Leio a **documentação** do projeto (sim, documentação importa)
- Identifico os **entry points** principais (onde o dado do usuário entra)
- Traço o caminho do dado pelo código, anotando cada transformação
- Procuro por **padrões perigosos**: conversões de tipo, alocações manuais de memória, parsing customizado, lógica de bounds checking
- Anoto **tudo** que parece estranho, mesmo que eu não entenda na hora

Voce não precisa entender 100% do código no primeiro dia. Na real, voce provavelmente **não vai** entender. E ta tudo bem. O entendimento vem com o tempo, e cada vez que voce volta no código voce enxerga coisas que antes passaram despercebidas.

Uma coisa que me ajudou **muito** foi usar ferramentas de navegação de código tipo o **Source Insight**, **Ghidra**, ou até o bom e velho **grep** mesmo. Ter a capacidade de pular entre funções e referências rapidamente faz uma diferença absurda quando voce ta tentando entender um codebase grande.

# Tomando notas (isso é ESSENCIAL)

Eu não consigo enfatizar isso o suficiente: **TOME NOTAS**. De tudo. Literalmente tudo. Cada ideia maluca que voce teve, cada função estranha que voce viu, cada hipótese que voce quer testar depois. Anota.

Por que? Porque a pesquisa é longa. Voce vai dormir, vai acordar no dia seguinte e **esquecer** aquela ideia genial que teve as 3 da manhã. Ou voce vai voltar depois de uma semana e não lembrar por que marcou aquela função como suspeita.

Eu pessoalmente uso um mix de **Notion** e **notas no próprio código** (comentários). Mas use o que funcionar pra voce, pode ser um txt, um caderno fisico, tanto faz. O importante é que esteja **registrado**.

O formato que eu gosto de usar nas minhas notas:

- **O que eu olhei hoje**: breve resumo do que analisei
- **Coisas suspeitas**: funções, padrões, comportamentos estranhos
- **Hipóteses**: o que eu acho que pode dar bug e por que
- **Próximos passos**: o que eu quero olhar amanhã

Isso parece bobo mas faz uma diferença **gigante** na continuidade da pesquisa. Voce não perde contexto entre os dias e consegue manter um progresso constante.

# Lidando com a frustração

Esse é o elefante na sala que ninguem fala. Fazer research é **frustrante**. Tem dias que voce vai passar 8 horas olhando código e não vai encontrar **nada**. Tem semanas que voce vai achar que ta no caminho certo e descobre que o "bug" que voce achou não é exploravel. Tem meses que voce simplesmente não acha nada.

E sabe o que? **Isso é normal**. Faz parte do processo. Os melhores pesquisadores do mundo também passam por isso, a diferença é que eles **não desistem**.

Algumas coisas que me ajudam a lidar com a frustração:

- **Lembre que cada hora de research te deixa melhor**, mesmo que voce não ache nada. Voce ta aprendendo o codebase, ta treinando seu olho, ta acumulando conhecimento.
- **Converse com outras pessoas** que fazem pesquisa. Trocar ideia com alguém que entende a dor faz muita diferença.
- **Faça pausas**. Serio. As vezes o melhor que voce pode fazer pela sua pesquisa é fechar o computador e ir fazer outra coisa. Muitas vezes a solução vem quando voce **não** ta ativamente pensando no problema.
- **Celebre as pequenas vitórias**. Entendeu uma função complexa? Vitória. Mapeou um entry point novo? Vitória. Não precisa ser um CVE pra contar como progresso.

# Usando AI como auxílio

Sim, eu uso AI na pesquisa e não tenho vergonha de falar isso. Mas é importante entender **como** usar. AI não vai encontrar o bug pra voce (pelo menos não ainda hehehe), mas ela pode te ajudar em varias coisas:

- **Entender código complexo**: joga um trecho de código e pede pra explicar o que faz
- **Brainstorming de attack vectors**: "dado esse componente que faz X, quais seriam possíveis vetores de ataque?"
- **Automatizar tarefas repetitivas**: scripts de fuzzing, parsers de logs, etc
- **Rubber duck debugging**: as vezes só de explicar o problema pra AI voce já percebe a resposta

Mas cuidado: **não confie cegamente** no que a AI te fala. Ela pode errar, pode alucinar, pode te dar uma falsa sensação de segurança. Sempre **valide** o que ela te diz com o código real.

Com isso espero que voce consiga alguns bugs hehehe