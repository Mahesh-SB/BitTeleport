```json
{
  "traceId": "4bf92f3577b34da6a3ce929d0e0e4736",
  "spans": [
    {
      "name": "ProcessOrder",
      "spanId": "00f067aa0ba902b7",
      "parentSpanId": null,
      "traceId": "4bf92f3577b34da6a3ce929d0e0e4736",
      "startTime": "2026-07-26T10:00:00.000Z",
      "endTime": "2026-07-26T10:00:00.185Z",
      "durationMs": 185,
      "status": "OK",
      "tags": {
        "order.id": "ORD-1234"
      }
    },
    {
      "name": "ValidateOrder",
      "spanId": "a1b2c3d4e5f60001",
      "parentSpanId": "00f067aa0ba902b7",
      "traceId": "4bf92f3577b34da6a3ce929d0e0e4736",
      "startTime": "2026-07-26T10:00:00.001Z",
      "endTime": "2026-07-26T10:00:00.051Z",
      "durationMs": 50,
      "status": "OK",
      "tags": {
        "order.id": "ORD-1234"
      },
      "events": [
        { "name": "Validation passed", "timestamp": "2026-07-26T10:00:00.050Z" }
      ]
    },
    {
      "name": "ChargePayment",
      "spanId": "a1b2c3d4e5f60002",
      "parentSpanId": "00f067aa0ba902b7",
      "traceId": "4bf92f3577b34da6a3ce929d0e0e4736",
      "startTime": "2026-07-26T10:00:00.052Z",
      "endTime": "2026-07-26T10:00:00.152Z",
      "durationMs": 100,
      "status": "OK",
      "tags": {
        "order.id": "ORD-1234",
        "payment.provider": "Stripe"
      }
    },
    {
      "name": "ShipOrder",
      "spanId": "a1b2c3d4e5f60003",
      "parentSpanId": "00f067aa0ba902b7",
      "traceId": "4bf92f3577b34da6a3ce929d0e0e4736",
      "startTime": "2026-07-26T10:00:00.153Z",
      "endTime": "2026-07-26T10:00:00.184Z",
      "durationMs": 31,
      "status": "OK",
      "tags": {
        "order.id": "ORD-1234"
      }
    },
    {
      "name": "GenerateShippingLabel",
      "spanId": "a1b2c3d4e5f60004",
      "parentSpanId": "a1b2c3d4e5f60003",
      "traceId": "4bf92f3577b34da6a3ce929d0e0e4736",
      "startTime": "2026-07-26T10:00:00.153Z",
      "endTime": "2026-07-26T10:00:00.183Z",
      "durationMs": 30,
      "status": "OK",
      "tags": {
        "carrier": "FedEx"
      }
    }
  ]
}

```
