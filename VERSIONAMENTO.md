# Controle de versões e atualização do mapa

## 1. O que é uma versão

Uma versão é uma edição completa do mapa, congelada num dia. Ela inclui os **dados**, as **funcionalidades** e o **design e a usabilidade**. Por isso cada versão leva duas datas:

- **Publicada em:** o dia em que a versão foi gerada e publicada.
- **Dados até:** a data de referência dos dados, ou seja, o limite das fontes consultadas.

Uma versão só de design pode mudar a data de publicação sem mudar a data dos dados. Os dois aparecem no selo do topo do mapa, na tela de senha e no botão Sobre.

## 2. Numeração (versionamento semântico)

A versão tem três números, **MAIOR.MENOR.CORREÇÃO** (ex.: 1.0.0). É o padrão usado em software, conhecido como *semantic versioning*.

| Sobe o número | Quando | Exemplos |
|---|---|---|
| MAIOR (1.x.x → 2.0.0) | Mudança de base, de método ou de estrutura: comparações com a versão anterior deixam de valer, ou o modo de usar muda bastante | Nova ADA ou novo eixo; nova base da Receita; nova regra de classificação; dados do campo do PTTS incorporados; reformulação geral da interface |
| MENOR (1.0.x → 1.1.0) | Algo novo que não quebra o que existia | Nova camada (contêineres da Codeca, redes do SAMAE); dados atualizados; nova função (formulário de campo, impressão por trecho); melhoria de usabilidade (novo filtro, legenda mais clara) |
| CORREÇÃO (1.0.0 → 1.0.1) | Conserto sem conteúdo novo | Nome ou ponto errado; texto, rótulo ou cor; defeito de exibição no celular |

Quando uma versão traz mudanças de vários tipos, vale o número mais alto. Por exemplo, uma camada nova com duas correções é MENOR.

## 3. Registro das mudanças (CHANGELOG.md)

Cada versão ganha um bloco no topo do CHANGELOG, com as categorias que se aplicarem:

- **Dados:** o que entrou, saiu ou foi atualizado, e de que fonte.
- **Funcionalidades:** o que dá para fazer de novo.
- **Design e usabilidade:** mudanças de aparência ou de forma de uso.
- **Segurança:** senha, LGPD, o que deixou de ser mostrado.
- **Correções:** o que estava errado.
- **Removido:** o que saiu.

O mesmo histórico aparece no botão Sobre do mapa.

## 4. Onde fica cada coisa

| Arquivo | Vai para o GitHub? | Para quê |
|---|---|---|
| index.html | Sim | O site (mapa protegido por senha) |
| versao.json | Sim | Versão e datas em texto simples |
| CHANGELOG.md | Sim | Histórico das mudanças |
| VERSIONAMENTO.md | Sim | Este guia |
| LEIA-ME.md | Sim | Resumo da pasta |
| mapa_sem_senha_NAO_PUBLICAR.html | Não | Cópia aberta da versão atual, de uso interno |
| arquivo/ | Não | Cópias abertas de versões antigas, de uso interno |
| .gitignore | Sim | Impede que o GitHub Desktop envie arquivos sem senha |

O GitHub guarda todas as versões anteriores do index.html (aba "History" do arquivo). Para voltar a uma versão, basta restaurá-la de lá.

## 5. Rotina de atualização

**Quem faz o quê:**
- **Equipe:** decide o que entra na próxima versão e aprova antes de publicar.
- **Claude (no Cowork):**
  - gera o mapa;
  - define o número da versão, seguindo a tabela acima;
  - escreve o CHANGELOG;
  - criptografa com a senha;
  - grava tudo na pasta Mapa_site.
- **Rodrigo (ou quem cuida do GitHub):** confere e publica.

**Passo a passo:**
1. Peça ao Claude: "gerar nova versão do mapa com [mudanças]". Informe a senha atual, ou peça para trocá-la.
2. Confira a pasta Mapa_site:
   - abra mapa_sem_senha_NAO_PUBLICAR.html no navegador;
   - veja se o selo mostra a versão e as datas certas;
   - veja se o CHANGELOG descreve as mudanças.
3. No GitHub Desktop, a aba "Changes" deve listar só arquivos que vão para o GitHub (tabela acima). Se aparecer algum "NAO_PUBLICAR", pare e verifique o .gitignore.
4. Em "Summary", escreva a versão e um resumo (ex.: "1.1.0 – camada de contêineres da Codeca") e clique em "Commit to main".
5. Clique em "Push origin". Em um ou dois minutos o site mostra a nova versão. Se o navegador mostrar a antiga, recarregue com Ctrl+F5.
6. Avise a equipe com a versão, a data dos dados e o resumo das mudanças.

## 6. Configuração inicial (uma vez só)

1. Instale o GitHub Desktop (desktop.github.com) e entre com a sua conta.
2. Clique em File, depois "Add local repository", e escolha a pasta Mapa_site. Ele vai avisar que a pasta ainda não é um repositório. Clique em "create a repository", com o nome `tunel-matteo`, e confirme.
3. Clique em "Publish repository". Pode desmarcar "Keep this code private": o mapa está criptografado.
4. No site do GitHub, abra o repositório, vá em Settings → Pages, escolha "Deploy from a branch", a branch `main` e a pasta `/ (root)`, e salve.
5. Anote o endereço do site e guarde a senha num gerenciador de senhas.

**Atenção:** a pasta Mapa_site está dentro do OneDrive. Isso funciona, mas evite editar os mesmos arquivos em dois computadores ao mesmo tempo, porque a sincronização do OneDrive pode conflitar com o Git. Se várias pessoas forem publicar, cada uma deve clonar o repositório numa pasta fora do OneDrive.

## 7. Senha

- **Troca:** a cada versão MAIOR, quando alguém sair da equipe, ou se a senha vazar.
- **Como trocar:** basta gerar a versão com a senha nova. O endereço do site continua o mesmo.
- **Repasse:** passe a senha por canal privado, nunca junto com o link.
