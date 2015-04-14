# asciidoctor-pdf-final-class

This repo shows how to provoke a "Cannot inherit from final class"-error when using asciidoctor-pdf in a gradle 
subproject where the nebula-info plugin is loaded.

First, verify that asciidoctor-pdf works by itself, as a standalone project. From the documentation subdirectory,
run "gradle -u clean asciidoctor". The "-u" option makes gradle consider this project as a standalone project,
ignoring the parent project. This should work.

    asciidoctor-pdf-final-class\documentation>gradle -u clean asciidoctor
    Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512m; support was removed in 8.0
    :clean UP-TO-DATE
    :asciidoctor
    Passing through unknown backend: pdf

    BUILD SUCCESSFUL

Next, verify that asciidoctor-pdf does not work when part of a subproject where the parent project has the nebula-info
plugin.

    asciidoctor-pdf-final-class\documentation>cd ..

    asciidoctor-pdf-final-class>gradle -u clean asciidoctor
    Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512m; support was removed in 8.0
    :documentation:clean
    :documentation:asciidoctor
    Passing through unknown backend: pdf
    :documentation:asciidoctor FAILED

    FAILURE: Build failed with an exception.

    * What went wrong:
    Execution failed for task ':documentation:asciidoctor'.
    > Cannot inherit from final class

    BUILD FAILED
