# Event-Integrator SDKs

Official SDKs for integrating Event-Integrator with your applications.

## Supported Languages

- **Go** - Native implementation with full async support
- **Python** - asyncio-compatible client
- **TypeScript** - Fully typed client for Node.js and browser

## Quick Start

### Go

```go
package main

import (
    "context"
    "github.com/similigh/event-integrator-sdk/go"
)

func main() {
    client := sdk.NewClient("http://localhost:8080")
    
    event := &sdk.Event{
        Type: "user.created",
        Data: map[string]interface{}{
            "user_id": "123",
            "email": "user@example.com",
        },
    }
    
    id, err := client.Submit(context.Background(), event)
    if err != nil {
        panic(err)
    }
    println("Event ID:", id)
}
```

### Python

```python
import asyncio
from event_integrator import AsyncClient

async def main():
    client = AsyncClient("http://localhost:8080")
    
    event = {
        "type": "user.created",
        "data": {
            "user_id": "123",
            "email": "user@example.com",
        }
    }
    
    event_id = await client.submit(event)
    print(f"Event ID: {event_id}")

asyncio.run(main())
```

### TypeScript

```typescript
import { EventIntegratorClient } from '@similigh/event-integrator-sdk';

async function main() {
    const client = new EventIntegratorClient('http://localhost:8080');
    
    const event = {
        type: 'user.created',
        data: {
            user_id: '123',
            email: 'user@example.com',
        }
    };
    
    const eventId = await client.submit(event);
    console.log('Event ID:', eventId);
}

main();
```

## Installation

### Go
```bash
go get github.com/similigh/event-integrator-sdk/go
```

### Python
```bash
pip install event-integrator
```

### TypeScript
```bash
npm install @similigh/event-integrator-sdk
```

## Features

All SDKs provide:
- **Type Safety**: Full type definitions and runtime validation
- **Error Handling**: Custom error types with retry classification
- **Retry Logic**: Configurable exponential backoff
- **Streaming**: Support for bulk event submission
- **Context**: Cancellation and timeout support

## Documentation

- [Go SDK Guide](docs/go-sdk.md)
- [Python SDK Guide](docs/python-sdk.md)
- [TypeScript SDK Guide](docs/typescript-sdk.md)
- [Common Patterns](docs/patterns.md)
- [Error Handling](docs/error-handling.md)

## Examples

See [examples/](examples/) directory for complete working examples:
- Webhook handlers
- Batch processing
- Error handling
- Testing patterns

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for development guidelines.

## License

MIT License - see LICENSE file for details
