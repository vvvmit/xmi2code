XMI-to-PHP XSL stylesheet
=========================

Beware! This is just a test and developpement branch.
It is not supposed to work for now.

How to try it?
--------------

For exemple: These are different ways to display a PHP code generated from XMI :

In command line With xsltproc :

    $ xsltproc php.xsl sample.xmi

With php :

    $xml = new DOMDocument;
    $xml->load('sample.xmi');
    
    $xsl = new DOMDocument;
    $xsl->load('php.xsl');
    
    $proc = new XSLTProcessor;
    $proc->importStyleSheet($xsl);
    echo $proc->transformToXML($xml);

With Java :

    import javax.xml.transform.stream.*;
    import javax.xml.transform.*;

    class XSLT {

      public static void main(String args[]){
        String xslt="php.xsl";
        String xml ="sample.xmi";
        try{
          TransformerFactory tFactory = TransformerFactory.newInstance();

          Transformer transformer = 
		    tFactory.newTransformer(new StreamSource(xslt));

          transformer.transform(new StreamSource(xml), 
			        new StreamResult(System.out));

        }
        catch (Exception e){
          e.printStackTrace();
        }
      }
    }


