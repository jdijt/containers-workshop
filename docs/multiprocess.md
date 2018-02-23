# Multiprocess containers

---
### Why (no) multiprocess?

- Bad:
    - Violates single responsibility principle.
    - Easy to get to invalid state.

- Good: (extremely) tightly coupled services.
    - Doesn't (really) violate single responsibility
    - Example: standalone kafka+zookeeper.



---
### Invalid state(s)

- Singleprocess
    - process failure = container failure.

- Naieve Multiprocess 
    - process failure _may_ cause container failure.

- Docker only monitors ONE process.

---
### Working with multiple processes

- Supervision must be done within container.
    - `Supervisord`.

- Think about failure modes!
    - Restart process
    - Kill whole container
