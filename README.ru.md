# Flagram MCP

> Рекламный маркетплейс Telegram-каналов, VK-сообществ и Max в виде MCP-сервера.

Поиск каналов и блогеров по тематике, аудитории, гео, языку и цене. Цены размещений, охваты постов, ER, CPV и аналитика подписчиков. Подходит для influencer-маркетинга, медиапланирования, таргетинга рекламных кампаний и конкурентного анализа.

🌐 Сайт: [flagram.com](https://flagram.com)
📦 Реестр: [`io.github.flagramtech/flagram-mcp`](https://registry.modelcontextprotocol.io/v0/servers?search=flagram-mcp)
🌍 Язык: [English](README.md) · **Русский**

---

## Что внутри

Удалённый MCP-сервер по Streamable-HTTP, отдающий каталог Flagram и флоу закупки рекламы в виде tool-ов:

| Группа | Tool-ы |
|---|---|
| **Поиск** | `searchChannels`, `searchPosts`, `searchAdvPosts`, `analyzeChannel` |
| **Кампании** | `listCampaigns`, `analyzeCampaign`, `getProjects` |
| **Корзина и оплата** | `getCartSummary`, `listCartItems`, `addCartItem`, `removeCartItem`, `cleanCart`, `checkoutCart` |
| **Словари** | `getCategories`, `getLanguages`, `getCountries`, `getCities`, `getPlatforms`, `getSalesChannels` |

Read-only-инструменты идемпотентны; операции с корзиной меняют состояние аккаунта.

## Адрес

```
https://mcp.flagram.com/mcp
```

Транспорт: `streamable-http` (JSON-RPC 2.0).
Авторизация: заголовок `Authorization: Bearer <api_token>` обязателен.

## Как получить токен

1. Войдите на [flagram.com](https://flagram.com).
2. Откройте **Настройки → API-токены** и создайте новый.
3. Скопируйте токен — повторно он не показывается.

## Подключение

### Claude Desktop / Code

```json
{
  "mcpServers": {
    "flagram": {
      "url": "https://mcp.flagram.com/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_TOKEN"
      }
    }
  }
}
```

### Cursor / любой MCP-клиент

Добавьте удалённый сервер:
- URL: `https://mcp.flagram.com/mcp`
- Header: `Authorization: Bearer YOUR_TOKEN`

## Рекомендуемый порядок вызовов

1. Получите id через `getCategories`, `getLanguages`, `getCountries` / `getCities`, `getPlatforms`.
2. Передайте эти id в `searchChannels` — получите список каналов.
3. Для глубокой статистики по каналу — `analyzeChannel`.
4. Подходящие позиции добавляйте через `addCartItem`, проверяйте `getCartSummary`, оформляйте `checkoutCart`.

## Поддержка

- Issues: [github.com/flagramtech/flagram-mcp/issues](https://github.com/flagramtech/flagram-mcp/issues)
- Email: support@flagram.com

## Лицензия

MIT
