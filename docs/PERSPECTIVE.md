### Some future tasks:  

I added some basic checks for the docker images, some linting for the kubernetes and terraform files. The next thing to go should definately be a strong focus on testing.
Maybe [terratest](https://terratest.gruntwork.io/) would be sufficient.  
Furthermore:
We should extend the pipeline to some basic tests against the fresh deployed pods in the kubernetes cluster.
There should be some test that verifies the basic functionality of the app. Maybe the team could help me to get more familiar with clojure so I would be able at least to set this app locally (and could maybe write some functional tests). This last suggestion needs to be bi-directional so I would suggest that from now on every CodeAsInfrastrucure story should be done in a pair programming session.
