# logger-unit-testing

```csharp
        private void SetupLogger()
        {
            _mockLogger.Setup(l => l.Log(It.IsAny<LogLevel>(),
                            It.IsAny<EventId>(),
                            It.IsAny<It.IsAnyType>(),
                            It.IsAny<Exception>(),
                            (Func<It.IsAnyType, Exception, string>)It.IsAny<object>()));
            _mockLogger.Setup(l => l.BeginScope(It.IsAny<Dictionary<string, object>>())).Returns(It.IsAny<IDisposable>());
        }

        private void VerifyLogger(LogLevel logLevel, string message)
        {
            _mockLogger.Verify(
             x => x.Log(
                 It.Is<LogLevel>(l => l == logLevel),
                 It.IsAny<EventId>(),
                 It.Is<It.IsAnyType>((v, t) => v.ToString().Contains(message)),
                 It.IsAny<Exception>(),
                 It.Is<Func<It.IsAnyType, Exception, string>>((v, t) => true)));
        }
````
