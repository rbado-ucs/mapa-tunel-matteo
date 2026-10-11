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
3. Abra https://github.com/rbado-ucs/mapa-tunel-matteo, clique em "Add file" → "Upload files" e arraste da pasta Mapa_site só os arquivos que mudaram e que vão para o GitHub (tabela acima). Nunca arraste "NAO_PUBLICAR" nem a pasta arquivo.
4. Em "Commit changes", escreva a versão e um resumo (ex.: "1.1.0 – camada de contêineres da Codeca") e clique em "Commit changes". Arquivos com o mesmo nome são substituídos.
5. Em um ou dois minutos o site mostra a nova versão. Se o navegador mostrar a antiga, recarregue com Ctrl+F5.
6. Avise a equipe com a versão, a data dos dados e o resumo das mudanças.

## 6. Configuração (feita em 11/10/2026)

- **Repositório:** https://github.com/rbado-ucs/mapa-tunel-matteo (público; o mapa está criptografado).
- **Site:** https://rbado-ucs.github.io/mapa-tunel-matteo/ (GitHub Pages, branch `main`, pasta `/ (root)`).
- **Publicação:** pelo navegador (passo a passo acima). O GitHub Desktop é opcional; se for usado, clone o repositório numa pasta fora do OneDrive, para evitar conflito entre a sincronização do OneDrive e o Git.
- **Senha:** guardada num gerenciador de senhas, fora desta pasta.

## 7. Senha

- **Troca:** a cada versão MAIOR, quando alguém sair da equipe, ou se a senha vazar.
- **Como trocar:** basta gerar a versão com a senha nova. O endereço do site continua o mesmo.
- **Repasse:** passe a senha por canal privado, nunca junto com o link.
