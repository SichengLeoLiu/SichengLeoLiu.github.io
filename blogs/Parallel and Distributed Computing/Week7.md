# Week 7

## MPI (Message Passing Interface)

`MPI_Init` is used to initialize the environment, and `MPI_Finalize` is used to terminate the environment.

A communicator defines a communication domain.

```C++
// Used to determine the number of processes
MPI_Comm_size(MPI_comm comm, int *size) 
// Process's rank
MPI_Comm_rank(MPI_comm comm, int *rank)
```
if we pass `MPI_COMM_WORLD` to `comm`, the program is going to use all processors.

```C++
MPI_Send(void *buf, int count, MPI_Datatype datatype, int dest, int tag, MPI_Comm comm)
MPI_Recv(void *buf, int count, MPI_Datatype datatype, int source, int tag, MPI_Comm comm, MPIStatus *status)
```
Processors can communicate only in the same communicator. MPI datatypes should be used when communication.

### Deadlocks
Break the circular wait.

- `MPI_Bcast()` can be used to broadcast. All processes must call it. 
- `MPI_Gather()` can be used to gather messages from all other processors. All processes need to send same amount of data.
- `MPI_Gatherv()`
- `MPI_Scatter()` divids dasta into `sendcount` parts, and send to other processors respectively.
- `MPI_Allgather()` all processors got all messages from others.
- `MPI_Reduce()` each processors have a set of data.