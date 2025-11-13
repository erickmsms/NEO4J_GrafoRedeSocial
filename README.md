# 📊 Análise de Rede Social - Projeto Neo4j

Este projeto implementa um sistema de análise de rede social utilizando o banco de dados de grafos Neo4j. O modelo permite explorar relações entre usuários, posts, engajamento e recomendações de conteúdo.

## 📁 Estrutura do Projeto

### Arquivos Principais:

1. **`1 - Criando Constraints.txt`** - Define as constraints de integridade do banco
2. **`2 - Povoamento Inicial.txt`** - Script de população inicial com dados de exemplo
3. **`3 - Criando Index.txt`** - Cria índices para otimização de consultas
4. **`4 - Perguntas de Negócio.txt`** - Consultas analíticas para insights de negócio
5. **`Vizualização.png`** - Diagrama visual da estrutura da rede

## 🎯 Objetivos do Projeto

- Modelar relações de rede social usando grafos
- Analisar engajamento e influência de usuários
- Fornecer recomendações de conteúdo e conexões
- Identificar padrões de comportamento na plataforma

## 🏗️ Modelo de Dados

### Nodes (Entidades):
- **User**: Usuários da plataforma
  - `id`, `username`, `name`, `join_date`, `location`, `verified`
- **Post**: Conteúdo publicado
  - `id`, `content`, `post_date`, `likes`, `shares`

### Relationships (Conectores):
- **FOLLOWS**: Relacionamento de seguimento entre usuários
- **CREATED**: Usuário criou um post
- **LIKED**: Usuário curtiu um post
- **SHARED**: Usuário compartilhou um post

## 🔧 Configuração e Implementação

### 1. Constraints de Integridade
```cypher
CREATE CONSTRAINT unique_user_username FOR (u:User) REQUIRE u.username IS UNIQUE;
CREATE CONSTRAINT unique_user_id FOR (u:User) REQUIRE u.id IS UNIQUE;
CREATE CONSTRAINT unique_post_id FOR (p:Post) REQUIRE p.id IS UNIQUE;
```

### 2. Índices de Performance
```cypher
CREATE INDEX post_likes_index FOR (p:Post) ON (p.likes);
CREATE INDEX post_shares_index FOR (p:Post) ON (p.shares);
CREATE INDEX post_date_index FOR (p:Post) ON (p.post_date);
```

## 📊 Análises e Consultas

### 1. **Usuários Mais Influentes**
Identifica usuários com maior engajamento baseado em likes e shares totais.

### 2. **Posts Mais Populares**
Ranking de posts por pontuação de engajamento (likes + shares × 2).

### 3. **Recomendações de Seguimento**
Sugere usuários para seguir baseado em conteúdo curtido em comum.

### 4. **Rede de Relacionamentos**
Mostra seguidores e seguidos de um usuário específico.

### 5. **Histórico de Atividades**
Analisa o comportamento dos usuários na plataforma.

### 6. **Performance de Conteúdo**
Calcula taxa de compartilhamento vs. curtidas por post.

## 👥 Dados de Exemplo

### Usuários:
- **Ana Silva** (@ana_silva) - São Paulo, Verificada
- **Carlos Lima** (@carlos_lima) - Rio de Janeiro, Verificado  
- **Maria Oliveira** (@maria_oliveira) - Belo Horizonte
- **João Santos** (@joao_santos) - Porto Alegre

### Posts:
- "Novo framework JavaScript lançado!" (Ana Silva)
- "Dicas de carreira em tecnologia" (Carlos Lima)
- "Receita de pão caseiro fácil" (Maria Oliveira)
- "Resenha do último filme" (João Santos)

## 🚀 Como Executar

1. Execute os scripts na ordem numérica:
   ```bash
   # 1. Constraints
   # 2. Povoamento
   # 3. Índices
   # 4. Consultas
   ```

2. Utilize o Neo4j Browser para visualizar os resultados

3. Modifique as consultas conforme necessário para suas análises

## 📈 Métricas de Engajamento

- **Engajamento Total**: Soma de likes e shares
- **Pontuação de Engajamento**: `likes + (shares × 2)`
- **Taxa de Compartilhamento**: `(compartilhamentos/curtidas) × 100`

## 💡 Casos de Uso

- **Marketing**: Identificar influenciadores naturais
- **Produto**: Melhorar recomendações de conteúdo
- **Growth**: Entender padrões de engajamento
- **Moderação**: Monitorar atividades dos usuários

---

*Projeto desenvolvido para demonstração de capacidades analíticas com Neo4j e modelagem de redes sociais.*
