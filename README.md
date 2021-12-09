# lucene-opennlp-lemmatizer-fix

This project packages the LUCENE-10171 fix as a separate project, until it's resolved/merged upstream.

To use this in existing Solr installations:

- Build the project `mvn clean package`
- Copy the generated `target/opennlp-lemmatizer-fix-1.0.jar` to Solr's lib directory
- replace any instances of `solr.OpenNLPLemmatizer` with `org.apache.lucene.analysis.opennlp.fix.OpenNLPLemmatizerFilterFactory`
  - eg: `<filter class="solr.OpenNLPLemmatizerFilterFactory" lemmatizerModel="en-lemmatizer.bin" dictionary="lemmas.txt"/>` 
  - becomes: `<filter class="org.apache.lucene.analysis.opennlp.fix.OpenNLPLemmatizerFilterFactory" lemmatizerModel="en-lemmatizer.bin" dictionary="lemmas.txt"/>`
- restart Solr 
