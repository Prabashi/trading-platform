# Trading Platform
Event-driven OMS: Gateway → Risk → Execution → venue; fills flow back. Decisions in docs/adr.

## Commands
- Infra: docker compose -f deploy/docker-compose.yml up -d
- Build: dotnet build    Test: dotnet test

## Rules (never break)
- Publish only through IOutbox, in the same DB transaction as the state change.
- Every consumer runs through the inbox; handlers must be idempotent.
- No service reads or writes another service's database.
- Money and quantities: decimal in C#, numeric(20,8) in SQL. Never double.
- Order state changes only through Order aggregate methods.

## Topics
orders.commands (key orderId), orders.events (key orderId),
executions.reports (key accountId), platform.dlq