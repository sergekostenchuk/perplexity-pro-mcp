# Perplexity Pro MCP

<!-- EN -->
High-performance MCP (Model Context Protocol) server for Perplexity API integration with multi-threading support.

<!-- RU -->
Высокопроизводительный MCP (Model Context Protocol) сервер для интеграции с Perplexity API с поддержкой многопоточности.

---

## 🔍 **Complete Functionality Overview** (EN)

### **Core Commands**

#### `search(query, options?)` 
Single query search with configurable options
- **Parameters**: query (required), model, max_tokens
- **Example**: `search("What is quantum computing?")`

#### `multiSearch(queries[], options?)`
Parallel execution of up to 5 searches simultaneously
- **Limit**: maximum 5 queries
- **Progress**: real-time progress tracking
- **Example**: `multiSearch(["AI trends", "Quantum computing", "Climate tech"])`

#### `deepResearch(topic, depth?)`
Multi-level topic exploration with automatic branching (1-3 levels)
- **Depth**: 1-3 levels (default: 2)
- **Branching**: up to 5 subtopics per level
- **Auto-analysis**: key insights extraction
- **Example**: `deepResearch("Future of renewable energy", 3)`

### **Specialized Commands**

#### `factCheck(statement)`
Fact verification with credible sources
- **Model**: sonar-pro for accuracy
- **Output**: true/false/partially true + sources

#### `codeSearch(query, language?)`
Code examples and documentation search
- **Languages**: optional programming language specification
- **Output**: code examples + documentation

#### `recentSearch(query, days?)`
Recent information search (default: 7 days)
- **Range**: 1-30 days
- **Focus**: news and latest developments

#### `academicSearch(query)`
Scientific papers and research search
- **Output**: academic sources + citations

### **Performance Features**

- **HTTP/2 Connection Pooling**: Minimal latency with persistent connections
- **Smart Caching**: Content-aware TTL strategies
- **Real-time Progress**: Visual feedback for long operations
- **Error Handling**: Automatic retries with exponential backoff
- **Performance Monitoring**: Built-in statistics and metrics

### **Benchmarks**
| Operation | p50 | p95 | p99 |
|-----------|-----|-----|-----|
| Single Search | 250ms | 500ms | 1200ms |
| Multi-Search (5) | 400ms | 800ms | 1500ms |
| Deep Research | 2000ms | 5000ms | 8000ms |

---

## 🔍 **Полное описание функционала** (RU)

### **Основные команды**

#### `search(query, options?)` 
Базовый поиск с одним запросом
- **Параметры**: query (обязательно), model, max_tokens
- **Пример**: `search("Что такое квантовые вычисления?")`

#### `multiSearch(queries[], options?)`
Параллельный поиск до 5 запросов одновременно
- **Лимит**: максимум 5 запросов
- **Прогресс**: отображение в реальном времени
- **Пример**: `multiSearch(["AI тренды", "Квантовые компьютеры", "Климат технологии"])`

#### `deepResearch(topic, depth?)`
Многоуровневое исследование темы (1-3 уровня глубины)
- **Глубина**: 1-3 уровня (по умолчанию 2)
- **Ветвление**: до 5 подтем на уровень
- **Автоанализ**: извлечение ключевых инсайтов
- **Пример**: `deepResearch("Будущее возобновляемой энергии", 3)`

### **Специализированные команды**

#### `factCheck(statement)`
Проверка фактов с источниками
- **Модель**: sonar-pro для точности
- **Выход**: правда/ложь/частично правда + источники

#### `codeSearch(query, language?)`
Поиск кода и документации
- **Языки**: опционально указать язык программирования
- **Результат**: примеры кода + документация

#### `recentSearch(query, days?)`
Поиск свежей информации (по умолчанию 7 дней)
- **Диапазон**: 1-30 дней
- **Фокус**: новости и последние разработки

#### `academicSearch(query)`
Поиск научных статей и исследований
- **Результат**: академические источники + цитаты

### **Особенности производительности**

- **HTTP/2 Connection Pooling**: Минимальная задержка через постоянные соединения
- **Smart Caching**: Контекстно-зависимое кеширование с разными TTL
- **Прогресс в реальном времени**: Визуальная обратная связь для длительных операций
- **Обработка ошибок**: Автоматические повторы с экспоненциальным backoff
- **Мониторинг производительности**: Встроенная статистика и метрики

### **Производительность**
| Операция | p50 | p95 | p99 |
|----------|-----|-----|-----|
| Одиночный поиск | 250ms | 500ms | 1200ms |
| Мульти-поиск (5) | 400ms | 800ms | 1500ms |
| Глубокое исследование | 2000ms | 5000ms | 8000ms |

---

## Features (EN)

- ⚡ **HTTP/2 Connection Pooling** - Minimal latency with persistent connections
- 🔄 **Parallel Search** - Execute up to 5 searches simultaneously
- 🧐 **Deep Research** - Multi-level exploration with automatic topic branching
- 💾 **Smart Caching** - Content-aware TTL strategies for optimal performance
- 📊 **Real-time Progress** - Visual feedback for long-running operations
- 🛡️ **Robust Error Handling** - Automatic retries with exponential backoff
- 📈 **Performance Monitoring** - Built-in statistics and metrics

## Installation

### Quick Install (Recommended)

```bash
npx @mlllm/perplexity-pro-mcp
```

This will:
- Check Node.js compatibility (requires v20+)
- Prompt for your Perplexity API key
- Test the API connection
- Configure Claude Desktop automatically
- Build and install the MCP server

### Manual Install

```bash
# Clone the repository
git clone https://github.com/sergekostenchuk/perplexity-pro-mcp.git
cd perplexity-pro-mcp

# Install dependencies
npm install

# Set your API key
export PERPLEXITY_API_KEY=your-api-key-here

# Build the project
npm run build

# Run the installer
npm run install-local
```

## Available Commands

### Main Search Commands

#### `search(query, options?)`
Perform a single search query.

```javascript
// In Claude Desktop
search("What are the latest developments in quantum computing?")

// With options
search("Explain transformer architecture", {
  model: "pplx-70b-online",
  max_tokens: 2000
})
```

#### `multiSearch(queries[], options?)`
Execute multiple searches in parallel (up to 5).

```javascript
multiSearch([
  "Latest AI breakthroughs 2024",
  "Quantum computing applications",
  "Climate technology innovations"
])
```

#### `deepResearch(topic, depth?)`
Perform comprehensive multi-level research on a topic.

```javascript
// Basic research (2 levels deep)
deepResearch("Future of renewable energy")

// Exhaustive research (3 levels)
deepResearch("CRISPR gene editing applications", 3)
```

### Specialized Commands

#### `factCheck(statement)`
Verify facts and claims with sources.

```javascript
factCheck("The moon landing happened in 1969")
```

#### `codeSearch(query, language?)`
Search for code examples and documentation.

```javascript
codeSearch("binary search implementation", "python")
codeSearch("React hooks best practices")
```

#### `recentSearch(query, days?)`
Find information from recent timeframes.

```javascript
recentSearch("OpenAI announcements", 7)
recentSearch("Stock market news", 1)
```

#### `academicSearch(query)`
Search academic papers and research.

```javascript
academicSearch("machine learning in healthcare")
```

### Utility Commands

- `help()` - Display all available commands with examples
- `stats()` - Show connection and cache statistics
- `config()` - Display current configuration
- `clearCache()` - Clear the response cache

## Configuration

### Environment Variables

```bash
PERPLEXITY_API_KEY=your-api-key-here
```

### Claude Desktop Configuration

The installer automatically adds this configuration:

```json
{
  "mcpServers": {
    "perplexity-pro": {
      "command": "node",
      "args": ["/path/to/perplexity-pro-mcp/dist/index.js"],
      "env": {
        "PERPLEXITY_API_KEY": "your-api-key"
      }
    }
  }
}
```

## API Client Usage

### TypeScript/JavaScript

```typescript
import { PerplexityClient } from '@mlllm/perplexity-pro-mcp';

const client = new PerplexityClient({
  apiKey: process.env.PERPLEXITY_API_KEY,
  maxConnections: 5,
  timeout: 30000,
});

// Simple search
const result = await client.search({
  query: 'What is quantum entanglement?',
  options: {
    model: 'pplx-70b-online',
    max_tokens: 1500,
  },
});

// Multi-search
const multiResults = await client.multiSearch(
  ['AI trends', 'Robotics advances', 'Neural interfaces'],
  { model: 'pplx-70b-online' }
);

// Stream responses
const stream = client.streamSearch({
  query: 'Explain machine learning',
  options: { stream: true }
});

for await (const chunk of stream) {
  process.stdout.write(chunk);
}

// Get statistics
console.log(client.getConnectionStats());
```

## Performance

### Benchmarks

| Operation | p50 Latency | p95 Latency | p99 Latency |
|-----------|-------------|-------------|-------------|
| Single Search | 250ms | 500ms | 1200ms |
| Multi-Search (5) | 400ms | 800ms | 1500ms |
| Deep Research | 2000ms | 5000ms | 8000ms |

### Caching Strategy

| Content Type | TTL | Use Case |
|--------------|-----|----------|
| Facts | 7 days | Historical information, definitions |
| News | 1 hour | Current events, breaking news |
| Code | 24 hours | Documentation, examples |
| Research | 3 days | Academic papers, studies |
| Recent | 15 minutes | Real-time data |

## Advanced Features

### Progress Tracking

Multi-search operations provide real-time progress updates:

```javascript
const results = await multiSearch([...queries], {
  showProgress: true
});

// Output:
// Processing batch 1
// ✓ Completed: "AI trends" (187ms)
// ✓ Completed: "Robotics" (234ms)
// ...
```

### Connection Pool Monitoring

```javascript
stats()

// Output:
// Active connections: 2
// Idle connections: 3
// Average response time: 267ms
// Cache hit rate: 67%
```

### Error Handling

The client implements intelligent retry logic:

- Network errors: 3 retries with exponential backoff
- Rate limits (429): Automatic throttling
- Server errors (5xx): Configurable retry attempts

## Development

### Project Structure

```
perplexity-pro-mcp/
├── src/
│   ├── index.ts          # MCP server entry point
│   ├── api/              # HTTP client implementation
│   ├── cache/            # Caching strategies
│   ├── engines/          # Search engines (multi, deep)
│   ├── mcp/              # MCP protocol handlers
│   └── utils/            # Logging and helpers
├── tests/                # Test suites
├── scripts/              # Installation scripts
└── dist/                 # Compiled output
```

### Running Tests

```bash
# Run all tests
npm test

# Watch mode
npm run test:watch

# Coverage report
npm run test:coverage
```

### Building

```bash
# Development build
npm run build

# Production build
npm run build:prod
```

## Troubleshooting

### Common Issues

1. **"API key is invalid"**
   - Verify your API key at https://www.perplexity.ai/settings/api
   - Ensure no extra spaces in the key

2. **"Claude Desktop not found"**
   - The installer will provide manual configuration steps
   - Check the config location for your OS

3. **"Connection timeout"**
   - Check your internet connection
   - Verify firewall settings allow HTTPS to api.perplexity.ai

4. **"Rate limit exceeded"**
   - The client automatically handles rate limits
   - Reduce parallel requests if persistent

### Debug Mode

Enable detailed logging:

```bash
export DEBUG=perplexity:*
export NODE_ENV=development
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

MIT License - see LICENSE file for details

## Acknowledgments

- Built for [Claude Desktop](https://claude.ai)
- Powered by [Perplexity AI](https://perplexity.ai)
- Uses the [Model Context Protocol](https://modelcontextprotocol.io)

---

**Version**: 2.0.0  
**Author**: kostenchuksergey  
**Repository**: [GitHub](https://github.com/sergekostenchuk/perplexity-pro-mcp)