1. Gathering System Requirements
   - As with any systems design interview question, the first thing that we want to do is to gather system requirements; we need to figure out what system we're building exactly.From the answers we were given to our clarifying questions (see Prompt Box), we're building a system that involves repeatedly (in the order of thousands of times per day) building and deploying code to hundreds of thousands of machines spread out across 5-10 regions around the world.
   - Building code will involve grabbing snapshots of source code using commit SHA identifiers; beyond that, we can assume that the actual implementation details of the building action are taken care of. In other words, we don't need to worry about how we would build JavaScript code or C++ code; we just need to design the system that enables the repeated building of code.
   - Building code will take up to 15 minutes, it'll result in a binary file of up to 10GB, and we want to have the entire deployment process (building and deploying code to our target machines) take at most 30 minutes.
   - Each build will need a clear end-state (SUCCESS or FAILURE), and though we care about availability (2 to 3 nines), we don't need to optimize too much on this dimension.

2. Coming Up With A Plan
   - It's important to organize ourselves and to lay out a clear plan regarding how we're going to tackle our design. What are the major, distinguishable components of our how system?
   - It seems like this system can actually very simply be divided into two clear subsystems:
        - the Build System that builds code into binaries
        - the Deployment System that deploys binaries to our machines across the world
    - Note that these subsystems will of course have many components themselves, but this is a very straightforward initial way to approach our problem.

3. Build System -- General Overview
   - From a high-level perspective, we can call the process of building code into a binary a job, and we can design our build system as a queue of jobs. Jobs get added to the queue, and each job has a commit identifier (the commit SHA) for what version of the code it should build and the name of the artifact that will be created (the name of the resulting binary). Since we're agnostic to the type of the code being built, we can assume that all languages are handled automatically here.
   - We can have a pool of servers (workers) that are going to handle all of these jobs. Each worker will repeatedly take jobs off the queue (in a FIFO manner—no prioritization for now), build the relevant binaries (again, we're assuming that the actual implementation details of building code are given to us), and write the resulting binaries to blob storage (Google Cloud Storage or S3 for instance). Blob storage makes sense here, because binaries are literally blobs of data.

4. Build System -- Job Queue
   - A naive design of the job queue would have us implement it in memory (just as we would implement a queue in coding interviews), but this implementation is very problematic; if there's a failure in our servers that hold this queue, we lose the entire state of our jobs: queued jobs and past jobs.
   - It seems like we would be unnecessarily complicating matters by trying to optimize around this in-memory type of storage, so we're likely better off implementing the queue using a SQL database.