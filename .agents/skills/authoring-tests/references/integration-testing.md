# Integration and lifecycle tests

Use actual component composition when behavior crosses a boundary. Keep the
fixture small enough to see inputs, event order, and expected output directly.
Avoid building a parallel application framework for tests.

Each test owns its files, ports, processes, and state, and cleans them up on
success and failure. Use isolated temporary directories and allocated ports.
Synchronize on observable conditions or controlled time; arbitrary sleeps hide
races. Bound waits and include useful failure evidence.

Exercise relevant startup, success, failure, retry, cancellation, restart, and
cleanup paths. Verify externally visible state and effects, not only internal
call counts. A timeout alone does not prove a remote operation never happened;
respect the real idempotency and recovery contract.

Keep deterministic offline cases separate from genuine external integration
runs. Label fixtures, local peers, and real services accurately. Use the actual
supported environment for operational qualification; a fake service cannot prove
that integration. Record versions, configuration, inputs, and cleanup outcomes.

If order-dependent failures occur, isolate shared state, repeat in different
orders, and reduce to the polluting case. Use the project's test runner rather
than embedding language-specific runner assumptions in reusable instructions.
