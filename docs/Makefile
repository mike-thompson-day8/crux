STYLESDIR = styles
STYLESHEET = juxt.css

index.html:	*.adoc ${STYLESDIR}/${STYLESHEET}
	asciidoctor -d book -a "webfonts!" -a stylesdir=${STYLESDIR} -a stylesheet=${STYLESHEET} index.adoc

docs.zip: index.html javadoc
	zip -r docs.zip index.html img/* javadoc/*

%.adoc:		%.md
	pandoc --atx-headers $< -o $@

crux.epub:	index.html
	pandoc $< -o $@

javadoc:
	javadoc -cp `cd ..; lein classpath` -d $@ -sourcepath ../src -exclude crux crux.api

clean:
	rm -rf index.html javadoc docs.zip
