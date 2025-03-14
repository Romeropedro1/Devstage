

# NLW Connect - API Client

Este projeto contém uma série de funções para interação com a API de inscrição e ranking do evento **NLW Connect**. A API permite que os usuários se inscrevam em um evento, visualizem seus rankings e acessem links de convite.

## Estrutura de Tipos e Funções

Este projeto contém os seguintes tipos e funções para interagir com os endpoints da API:

### Tipos

1. **SubscribeToEventBody**  
   Tipo para o corpo da requisição de inscrição ao evento.

   ```typescript
   export type SubscribeToEventBody = {
     name: string;
     email: string;
     referrer?: string | null;
   };
   ```

2. **SubscribeToEvent201**  
   Resposta da requisição de inscrição.

   ```typescript
   export type SubscribeToEvent201 = {
     subscriberId: string;
   };
   ```

3. **GetRanking200RankingItem**  
   Tipo para cada item do ranking.

   ```typescript
   export type GetRanking200RankingItem = {
     id: string;
     name: string;
     score: number;
   };
   ```

4. **GetRanking200**  
   Resposta contendo o ranking de todos os participantes.

   ```typescript
   export type GetRanking200 = {
     ranking: GetRanking200RankingItem[];
   };
   ```

5. **GetSubscriberInviteCount200**  
   Contagem de convites feitos por um inscrito.

   ```typescript
   export type GetSubscriberInviteCount200 = {
     count: number;
   };
   ```

6. **GetSubscriberInviteClicks200**  
   Contagem de cliques nos convites de um inscrito.

   ```typescript
   export type GetSubscriberInviteClicks200 = {
     count: number;
   };
   ```

7. **GetSubscriberRankingPosition200**  
   Posição no ranking de um inscrito.

   ```typescript
   export type GetSubscriberRankingPosition200 = {
     position: number | null;
   };
   ```

### Funções

As funções disponíveis são:

#### `subscribeToEvent`

Inscreve um usuário no evento.

```typescript
export const subscribeToEvent = async (subscribeToEventBody: SubscribeToEventBody, options?: RequestInit): Promise<SubscribeToEvent201>;
```

- **URL**: `http://localhost:3333/subscriptions`
- **Método**: `POST`

#### `accessInviteLink`

Acessa o link de convite de um inscrito.

```typescript
export const accessInviteLink = async (subscriberId: string, options?: RequestInit): Promise<unknown>;
```

- **URL**: `http://localhost:3333/invites/{subscriberId}`
- **Método**: `GET`

#### `getRanking`

Obtém o ranking completo de inscritos.

```typescript
export const getRanking = async (options?: RequestInit): Promise<GetRanking200>;
```

- **URL**: `http://localhost:3333/ranking`
- **Método**: `GET`

#### `getSubscriberInviteCount`

Obtém a contagem de convites feitos por um inscrito.

```typescript
export const getSubscriberInviteCount = async (subscriberId: string, options?: RequestInit): Promise<GetSubscriberInviteCount200>;
```

- **URL**: `http://localhost:3333/subscribers/{subscriberId}/ranking/count`
- **Método**: `GET`

#### `getSubscriberInviteClicks`

Obtém a contagem de cliques nos convites de um inscrito.

```typescript
export const getSubscriberInviteClicks = async (subscriberId: string, options?: RequestInit): Promise<GetSubscriberInviteClicks200>;
```

- **URL**: `http://localhost:3333/subscribers/{subscriberId}/ranking/clicks`
- **Método**: `GET`

#### `getSubscriberRankingPosition`

Obtém a posição de um inscrito no ranking.

```typescript
export const getSubscriberRankingPosition = async (subscriberId: string, options?: RequestInit): Promise<GetSubscriberRankingPosition200>;
```

- **URL**: `http://localhost:3333/subscribers/{subscriberId}/ranking/position`
- **Método**: `GET`

---

## Como Usar

1. **Instalação**

   Clone este repositório e instale as dependências:

   ```bash
   git clone https://github.com/SeuUsuario/Devstage.git
   cd Devstage
   npm install
   ```

2. **Exemplo de uso**

   Para inscrever um usuário no evento:

   ```typescript
   const response = await subscribeToEvent({ name: "João", email: "joao@exemplo.com" });
   console.log(response.subscriberId);
   ```

3. **Ver Ranking**

   Para obter o ranking dos participantes:

   ```typescript
   const ranking = await getRanking();
   console.log(ranking);
   ```

---

## Contribuição

Se você deseja contribuir para o projeto, siga as etapas abaixo:

1. Faça um fork do repositório.
2. Crie uma branch para sua feature (`git checkout -b minha-feature`).
3. Faça o commit das suas alterações (`git commit -am 'Adicionando nova feature'`).
4. Envie a branch para o seu fork (`git push origin minha-feature`).
5. Abra um pull request.

---

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE). 

