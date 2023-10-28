# Convenções de Commits Convencionais para o OpenBlog

As Convenções de Commits Convencionais no projeto OpenBlog ajudam a manter um histórico de commits explícito e facilitam a geração automática de CHANGELOGs. Essas convenções descrevem os tipos de commits, âmbitos opcionais e alterações incompatíveis para comunicar as alterações no código de forma eficaz.

## Estrutura das Mensagens de Commit

Uma mensagem de commit no OpenBlog deve seguir a seguinte estrutura:

```
<tipo>[âmbito opcional]: <descrição>

[corpo opcional]

[rodapé(s) opcional(is)]
```

A mensagem de commit contém os seguintes elementos estruturais para comunicar a intenção aos consumidores do OpenBlog:

- **fix**: Use esse tipo para correções de bugs no código (correlaciona-se com PATCH no Versionamento Semântico).
- **feat**: Use esse tipo para introduzir novas funcionalidades no OpenBlog (correlaciona-se com MINOR no Versionamento Semântico).
- **BREAKING CHANGE**: Use esse tipo para comunicar alterações incompatíveis com a API (correlaciona-se com MAJOR no Versionamento Semântico). Alterações incompatíveis podem ser parte de commits de qualquer tipo.

Outros tipos de commits, além de fix e feat, são permitidos no OpenBlog. Por exemplo, você pode usar build, chore, ci, docs, style, refactor, perf, test e outros tipos, conforme necessário.

Os rodapés, incluindo BREAKING CHANGE: <descrição>, podem ser fornecidos e seguem um formato semelhante ao padrão de trailer do Git.

## Exemplos

### Commit com Descrição e Rodapé de Alteração Incompatível

```
feat(blog): adicionar funcionalidade de comentários

BREAKING CHANGE: A estrutura do banco de dados foi alterada para suportar comentários.
```

### Commit com ! para Destacar a Alteração Incompatível

```
feat(blog)!: adicionar funcionalidade de pesquisa global
```

### Commit com Âmbito e ! para Destacar a Alteração Incompatível

```
fix(security)!: corrigir vulnerabilidade de segurança
```

### Commit com Ambos ! e Rodapé de Alteração Incompatível

```
chore!: atualizar dependências

BREAKING CHANGE: As dependências agora exigem versões mais recentes.
```

### Commit sem Corpo

```
docs: atualizar documentação de instalação
```

### Commit com Âmbito

```
style(css): melhorar estilos de botões
```

### Commit com Corpo de Múltiplos Parágrafos e Múltiplos Rodapés

```
fix: corrigir vazamento de memória

O vazamento de memória ocorria devido a alocações não liberadas na função principal. Esta correção resolve o problema e melhora o desempenho geral.

Reviewed-by: Alice
Refs: #321
```

## Especificação

A especificação usa termos como "DEVE", "NÃO DEVE", "OBRIGATÓRIO", "DEVERÁ", "NÃO DEVERÁ", "DEVERIA", "NÃO DEVERIA", "RECOMENDADO", "PODE" e "OPCIONAL" conforme descrito no RFC 2119.

- Os commits DEVEM ser prefixados com um tipo, que consiste em um substantivo, como feat, fix, etc., seguido pelo âmbito OPCIONAL, ! OPCIONAL e do terminal necessário de dois pontos e espaço.
- O tipo feat DEVE ser usado quando um commit adiciona uma nova funcionalidade ao OpenBlog.
- O tipo fix DEVE ser usado quando um commit representa uma correção de bug no OpenBlog.
- Um âmbito PODE ser fornecido após um tipo. Um âmbito DEVE consistir em um substantivo que descreve uma seção do código entre parênteses, por exemplo, feat(blog):
- Uma descrição DEVE seguir imediatamente os dois pontos e espaço após o prefixo tipo/âmbito. A descrição é um resumo breve das alterações de código, por exemplo, fix: corrigir vulnerabilidade de segurança.
- Um corpo de commit mais longo PODE ser fornecido após a descrição breve, fornecendo informações contextuais adicionais sobre as alterações de código. O corpo DEVE começar uma linha em branco após a descrição.
- Um corpo de commit é de formato livre e PODE consistir em qualquer número de parágrafos separados por novas linhas.
- Um ou mais rodapés PODEM ser fornecidos uma linha em branco após o corpo. Cada rodapé DEVE consistir em um token de palavra, seguido de :<espaço> ou <espaço># separador, seguido de um valor de string (isso é inspirado na convenção de trailers do Git).
- O token de um rodapé DEVE usar - no lugar de caracteres de espaço em branco, por exemplo, Acked-by (isso ajuda a diferenciar a seção de rodapé do corpo de vários parágrafos). É feita uma exceção para BREAKING CHANGE, que PODE ser usado como token.
- O valor de

 um rodapé PODE conter espaços e novas linhas, e a análise DEVE terminar quando o próximo par de token/separador válido for observado.
- Alterações incompatíveis DEVEM ser indicadas no prefixo tipo/âmbito de um commit ou como uma entrada no rodapé.
- Se incluídas como um rodapé, uma alteração incompatível DEVE consistir no texto em maiúsculas ALTERAÇÃO INCOMPATÍVEL, seguido por dois pontos, espaço e uma descrição, por exemplo, ALTERAÇÃO INCOMPATÍVEL: a estrutura do banco de dados foi alterada.
- Se incluídas no prefixo tipo/âmbito, as alterações incompatíveis DEVEM ser indicadas por um ! imediatamente antes dos dois pontos. Se o ! for usado, o BREAKING CHANGE PODE ser omitido da seção de rodapé, e a descrição do commit DEVE ser usada para descrever a alteração incompatível.
- Tipos diferentes de feat e fix PODEM ser usados em mensagens de commit, por exemplo, docs: atualizar documentação de instalação.
- As unidades de informação que compõem os Commits Convencionais NÃO DEVEM ser tratadas como sensíveis a maiúsculas pelos implementadores, com exceção de ALTERAÇÃO INCOMPATÍVEL, que DEVE estar em maiúsculas.
- BREAKING-CHANGE DEVE ser sinônimo de ALTERAÇÃO INCOMPATÍVEL quando usado como um token em um rodapé.

## Por que Usar Commits Convencionais no OpenBlog

As vantagens de usar Commits Convencionais no projeto OpenBlog incluem:

- Geração automática de CHANGELOGs.
- Determinação automática de uma atualização semântica com base nos tipos de commits lançados.
- Comunicação eficaz da natureza das alterações aos membros da equipe e outras partes interessadas.
- Facilitação da contribuição de outros desenvolvedores ao projeto, permitindo que eles entendam o histórico de commit de forma clara e organizada.
