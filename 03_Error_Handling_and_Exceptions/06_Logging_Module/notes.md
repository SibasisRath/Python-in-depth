# Logging Module

## Explanation

The `logging` module provides a flexible framework for emitting log messages from Python programs. It allows you to track events that happen while software runs, which is essential for debugging and monitoring.

### Logging Levels

- `DEBUG`: Detailed information, typically of interest only when diagnosing problems.
- `INFO`: Confirmation that things are working as expected.
- `WARNING`: An indication that something unexpected happened, or indicative of some problem in the near future (e.g., ‘disk space low’). The software is still working as expected.
- `ERROR`: Due to a more serious problem, the software has not been able to perform some function.
- `CRITICAL`: A serious error, indicating that the program itself may be unable to continue running.

### Core Components

- **Logger**: Entry point for logging. You can create multiple loggers using `logging.getLogger(name)`.
- **Handler**: Sends log records to the appropriate destination (console, file, network, etc.). Common handlers include `StreamHandler`, `FileHandler`, `RotatingFileHandler`.
- **Formatter**: Specifies the layout of log messages.
- **Filter**: Provides a finer grained facility for determining which log records to output.

### Basic Configuration

```python
import logging

logging.basicConfig(level=logging.INFO)
logging.info("This is an info message")
logging.error("This is an error message")
```

### Advanced Configuration

```python
import logging

logger = logging.getLogger("myapp")
logger.setLevel(logging.DEBUG)

# create console handler with a higher log level
ch = logging.StreamHandler()
ch.setLevel(logging.WARNING)

# create file handler which logs even debug messages
fh = logging.FileHandler("app.log")
fh.setLevel(logging.DEBUG)

# create formatter and add it to the handlers
formatter = logging.Formatter("%(asctime)s - %(name)s - %(levelname)s - %(message)s")
ch.setFormatter(formatter)
fh.setFormatter(formatter)

# add the handlers to logger
logger.addHandler(ch)
logger.addHandler(fh)

logger.debug("debug message")
logger.info("info message")
logger.warning("warning message")
logger.error("error message")
logger.critical("critical message")
```

### Rotating Logs

```python
from logging.handlers import RotatingFileHandler

logger = logging.getLogger("myapp")
logger.setLevel(logging.DEBUG)
handler = RotatingFileHandler("app.log", maxBytes=2000, backupCount=5)
logger.addHandler(handler)

for i in range(1000):
    logger.debug(f"Line {i}")
```

## Tasks

### Beginner

1. Configure a basic logger that prints messages to the console.
2. Log messages at different levels and observe the output.
3. Write a script that logs exceptions using `logging.exception()`.

### Intermediate

1. Set up a logger with both console and file handlers.
2. Create a custom formatter that includes the module name and line number.
3. Use filters to only log messages from a certain module or above a certain level.

### Advanced

1. Implement a logging configuration using `dictConfig` or `fileConfig`.
2. Create a logging setup for a multithreaded application, ensuring thread-safety.
3. Build a log rotation strategy using `TimedRotatingFileHandler` and analyze old logs.
4. Integrate logging with exception chaining to automatically log full error chains.

## Quick Review

- **Levels**: DEBUG, INFO, WARNING, ERROR, CRITICAL
- **Logger**: Obtain with `getLogger()`
- **Handlers**: Console, file, rotating, etc.
- **Formatters**: Customize the message format
- **Configuration**: `basicConfig`, manual setup, or config files
- **Best Practice**: Use appropriate levels and avoid printing sensitive information