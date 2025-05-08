# REPRODUCER FOR eclipse/webtools.common#13

When trying to deploy the `warproject` into a servlet container the `with-fragments` jar file is excluded from the deployable, **UNLESS** you close the `with-fragments` project in the project explorer and let it be resolved through the local maven repository as an installed jar.

## Steps

1. checkout the project `gh repo clone dashorst/webtools.common-13`
2. build the project and install the artifacts into the local repository using maven
3. `cd webtools.common-13`
4. `mvn install`
5. import the projects into your Eclipse installation

The project structure:
<img width="347" alt="image" src="https://github.com/user-attachments/assets/6bb4f198-7619-41d1-9bf2-fac3550950db" />

6. try to deploy the `warproject` into your container (at least Wildfly 26+ doesn't work)
7. notice that the `warproject` misses the `with-fragments` jar file

A screen shot of step 6 and 7:
<img width="588" alt="image" src="https://github.com/user-attachments/assets/714bb8b9-51fa-46d1-8b13-a814ffa9bd0e" />

To mitigate the deployable issue follow these steps:

8. close the `with-fragments` project in the project explorer
9. try to deploy the `warproject` into your container
10. notice that the `warproject` now contains the `with-fragments` jar file

A screen shot of steps 8-10:
<img width="812" alt="image" src="https://github.com/user-attachments/assets/beecf595-4a72-4cb5-b8cd-9781e4185b78" />
