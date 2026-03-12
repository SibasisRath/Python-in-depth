# Logging and Monitoring

## Explanation

Logging and monitoring are essential for observing application behavior and diagnosing issues in production.

- Use Python’s built-in `logging` module with appropriate log levels (DEBUG, INFO, WARNING, ERROR, CRITICAL).
- Structured logging (JSON) can be easier to parse.
- Send logs to external systems (ELK stack, Splunk) or cloud services (CloudWatch).
- Monitoring tools include Prometheus, Grafana, New Relic, Datadog.

## Examples

### Basic logging setup
```python
import logging

logging.basicConfig(level=logging.INFO, format='%(asctime)s %(levelname)s %(message)s')
logger = logging.getLogger(__name__)

logger.info('Application started')
```

### Structured JSON logging
```python
import logging
import json

class JsonFormatter(logging.Formatter):
    def format(self, record):
        data = record.__dict__.copy()
        return json.dumps({k: data[k] for k in ('levelname', 'message', 'asctime')})

handler = logging.StreamHandler()
handler.setFormatter(JsonFormatter())
logging.getLogger().addHandler(handler)
```

## Tasks

### Beginner
1. Add logging to an existing script, using different levels for events.
2. Redirect logs to a file and rotate them using `logging.handlers.RotatingFileHandler`.

### Intermediate
1. Integrate logging with an external service (e.g., send logs to Graylog).
2. Create custom log filters or handlers.

### Advanced
1. Set up Prometheus metrics in a Python service and visualize with Grafana.
2. Implement health checks and alerts for key metrics.

## Quick Review
- Why should you include log levels and timestamps?
- What is the advantage of structured logging?

---