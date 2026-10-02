# Projeto Ryeland — decisões de leiaute

## Contexto e objetivo

**Instituição:** Instituto Federal do Ceará, Campus Aracati.  
**Professor orientador:** Felipe Bastos.  
**Equipe:** Francisco Gustavo, Noan Guedes, Nicollas de França e Daniel Lima.

O Ryeland propõe apoiar a criação de ovinos e caprinos na região de Tauá-CE. O foco é organizar o manejo, acompanhar a produção de carne, identificar candidatos à seleção genética, planejar transportes e melhorar a relação com compradores. Esta entrega é um protótipo acadêmico, não um sistema operacional de gestão pecuária.

## Planejamento das telas

A navegação se divide em sete áreas: visão geral, meu rebanho, seleção genética, logística, agenda, clientes e sobre o projeto. O painel inicial responde a três perguntas: como está a propriedade, quais animais precisam de acompanhamento e o que deve acontecer hoje.

Os arquivos de planejamento e imagens estão no diretório `assets/`:

- `leiaute-visao-geral.svg`: composição do painel, indicadores e agenda;
- `leiaute-rebanho.svg`: filtros, tabela e fluxo de cadastro;
- `rebanho.jpg`: fotografia ilustrativa utilizada no painel.
- `captura-desktop.png` e `captura-mobile.png`: capturas da implementação em 1440 px e 390 px de largura.

Os SVGs são leiautes esquemáticos criados diretamente em formato vetorial. Não são capturas de tela nem arquivos exportados do Canva/Figma; podem ser importados em uma ferramenta de design para revisão pela equipe.

## Relação entre o tema e as escolhas

### 1. Identificação e acompanhamento do rebanho

A tabela mostra identificação individual, nome, raça, espécie, sexo, idade, peso e fase de produção. A identificação distingue animais de nomes iguais. Separar ovinos e caprinos favorece a organização sem presumir que as duas espécies têm o mesmo manejo.

Santa Inês, Dorper, Boer e Anglo-Nubiana aparecem como exemplos, não como recomendações de raça para qualquer propriedade. Adaptação ao semiárido, disponibilidade alimentar, aptidão, sanidade e assistência técnica precisam orientar decisões reais. O formulário permite registrar animais sem raça definida.

O peso e a idade ajudam no acompanhamento de crescimento e engorda, mas um peso isolado não comprova produtividade ou prontidão para abate. Uma versão operacional precisará de histórico de pesagens, ganho médio diário, condição corporal e avaliação técnica.

### 2. Seleção genética e leilões

A seleção genética recebe uma tela própria, pois possui objetivos diferentes da produção para corte. Os cartões apresentam candidatos **em avaliação**, e não animais de mérito genético comprovado.

Genealogia, desempenho, avaliação reprodutiva, sanidade e critérios zootécnicos devem fundamentar a seleção. Essas informações ainda não estão implementadas; a tela explicita essa limitação. Evitamos inventar índices genéticos ou atribuir superioridade com base apenas em aparência ou peso.

### 3. Manejo e agenda

Vacinação, pesagem e visita de comprador são exemplos de compromissos. A agenda aparece no painel para manter o cuidado diário visível. A conclusão das tarefas é interativa, mas vale somente durante a sessão.

Datas e procedimentos sanitários são demonstrativos. O calendário real deve ser elaborado com orientação veterinária e considerar a situação sanitária da propriedade. O protótipo não recomenda medicamentos, doses nem protocolos universais.

### 4. Logística responsável

A tela apresenta data, finalidade, origem, destino, quantidade e situação da movimentação. Ela lembra a necessidade de conferir a Guia de Trânsito Animal (GTA), exigências sanitárias e bem-estar antes do embarque.

Planejar transporte também envolve adequação do veículo, lotação, separação dos grupos, manejo sem violência e cuidados compatíveis com a duração do percurso e o clima. O protótipo não emite GTA nem certifica regularidade documental. As localidades e operações comerciais são fictícias.

### 5. Relação com clientes

Compradores de reprodutores, parceiros de comercialização de carne e criadores interessados em matrizes têm necessidades distintas. A listagem explicita o perfil e o próximo contato de cada parceiro. Uma versão futura poderá registrar preferências, histórico de negociações e condições de entrega com proteção dos dados pessoais.

## Identidade visual e usabilidade

- **Verde profundo:** organiza a navegação e destaca ações principais, remetendo ao cuidado e à atividade rural.
- **Terracota e tons naturais:** acrescentam calor à interface e aparecem em informações de engorda e manejo.
- **Fundo claro e espaços amplos:** separam assuntos e evitam que a página inicial se transforme em uma lista única de dados.
- **Manrope e DM Sans:** fontes públicas, escolhidas para títulos claros e informações compactas.
- **Status com texto:** o significado não depende apenas de cores.
- **Ícones vetoriais:** reforçam os rótulos sem substituí-los.
- **Responsividade:** a navegação vira menu lateral em telas pequenas; tabelas permitem rolagem horizontal e cartões se reorganizam.
- **Interações:** botões com nomes acessíveis, foco visível, formulários com rótulos e validação nativa; diálogos usam o elemento nativo `dialog`, com fechamento por Escape.

A fotografia mostra um rebanho de ovinos e é exclusivamente ilustrativa. Ela não documenta a Caatinga, uma fazenda de Tauá ou as raças listadas. Em uma entrega regional definitiva, preferir fotografias autorizadas de produtores locais, com animais e paisagem do semiárido.

**Crédito da fotografia:** Andrea Lightfoot / Unsplash.  
**Arquivo servido:** https://images.unsplash.com/photo-1602027438676-ad64751bdbc1

## Componentes e funcionalidades implementadas

- Navegação entre as sete telas do protótipo;
- Indicadores ilustrativos da propriedade;
- Cadastro de animais com persistência no navegador (`localStorage`);
- Busca por nome, identificação ou raça e filtros por espécie;
- Consulta de ficha individual;
- Exportação dos animais cadastrados em CSV;
- Conclusão e reabertura de tarefas da agenda;
- Seleção de dias no calendário;
- Painéis de notificações, orientação e perfil demonstrativos;
- Página sobre a proposta e sua equipe.

Os indicadores de uma propriedade fictícia com 248 animais são uma simulação visual independente do pequeno cadastro de exemplo. Os novos cadastros incrementam o total de demonstração; não há processamento zootécnico real. Clima e datas também são ilustrativos.

## Implementação e requisito Next.js

A base fornecida é React 19 + Vite + Tailwind CSS v4, com pré-visualização supervisionada pelo Figma Make. Ela foi preservada para manter a aplicação funcional nesse ambiente. **Esta entrega não utiliza Next.js e, portanto, não conclui esse requisito da atividade.**

Para a etapa Next.js, propomos transformar as áreas em rotas do App Router: `/`, `/rebanho`, `/genetica`, `/logistica`, `/agenda`, `/clientes` e `/sobre`. A navegação e o cabeçalho poderão compor o leiaute compartilhado; os formulários e controles de estado serão componentes cliente. A migração exigirá revisão da persistência e testes próprios, não apenas a troca de nomes de arquivos.

Não há backend, login, integração meteorológica, controle de acesso ou sincronização. Os dados locais podem ser perdidos ao limpar o navegador. O protótipo não deve armazenar dados reais sensíveis.

## Proposta de apresentação em sala

A data e o tempo de apresentação não constam no material recebido. Ajustar o roteiro às orientações do professor.

| Integrante | Bloco sugerido | Demonstração |
| --- | --- | --- |
| Francisco Gustavo | Problema regional, público e hierarquia do painel | Visão geral e decisões de prioridade |
| Noan Guedes | Identificação individual e manejo | Cadastro, filtros, ficha e agenda |
| Nicollas de França | Seleção genética, leilões e transporte | Candidatos em avaliação e logística |
| Daniel Lima | Clientes, componentes e limites técnicos | Responsividade, CSV e evolução para Next.js |

Essa divisão é uma sugestão, **não uma declaração de participação já realizada**. Cada integrante deve revisar as telas, propor ajustes e registrar suas contribuições reais. A apresentação deve relatar decisões compartilhadas, dificuldades e alternativas discutidas, evitando atribuir trabalho não realizado.

### Sequência sugerida

1. Explicar o contexto de Tauá e distinguir ovinos, caprinos, corte e reprodução.
2. Apresentar os esquemas de leiaute e justificar a organização das telas.
3. Demonstrar um cadastro, filtro por espécie, ficha e exportação.
4. Mostrar a agenda e a logística com cuidados sanitários e documentais.
5. Explicar por que candidatos em avaliação não equivalem a mérito genético comprovado.
6. Encerrar com limites atuais e próximos passos: pesquisa com produtores, validação com profissionais, Next.js e backend.

## Pesquisa e validação pendentes

As decisões demonstram uma modelagem inicial do domínio, mas não substituem pesquisa de campo. Para sustentar a entrega final, consultar produtores de Tauá e materiais técnicos da Embrapa Caprinos e Ovinos; confirmar as normas de trânsito animal com a ADAGRI e validar questões sanitárias com profissionais habilitados. Registrar as fontes efetivamente lidas e as entrevistas realizadas, sem apresentar esta sugestão como pesquisa já concluída.
