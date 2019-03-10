# longrunner
Long-running task orchestration, backed by a database.

## Scenarios
- Schedule tasks for the `volman` project (<https://github.com/rinworks/volman>)to keep replica volumes up-to-date. This is the driving scenario - our first and only client at the moment. One or more
 worker tasks spawn on available hosts and go about keeping volumes up-to-date and checking up
 on remote backup drives. It involves both actively computing checksums and copying volumes as 
 well as requesting human operators to perform tasks such as bringing in volumes from a remote
 location or switching out a failed hard drive.
- Coordinate activities between multiple entities when capturing image and videos as part of
 the `cmrig` and `periscope` projects.


## Criteria
- Python libraries as `volman` is written in Python.
- MongoDB used for persistent store because we have some domain knowledge in MongoDB. However,
  if it is not too much overhead, define a "persistence" API layer to the database potentially
  allowing multiple database options.
- Can take on an assumption of using Docker containers if that provides a lot of benefit.
- Keep open the option of scheduling tasks on a Raspberry Pi, though that is not a requirement for
  `volman`. This is because we anticipate using Pis with the `cmrig` and `periscope` projects.
