.. _-decodeRequest-:

decodeRequest
=============

Tries to decode the request with the specified ``Decoder`` or rejects the request with an
``UnacceptedRequestEncodingRejection(supportedEncoding)``.

Signature
---------

.. includecode:: /../spray-routing/src/main/scala/spray/routing/directives/EncodingDirectives.scala
   :snippet: decodeRequest

Description
-----------

The ``decodeRequest`` directive is the building block for the ``decompressRequest`` directive.

``decodeRequest`` and ``decompressRequest`` are related like this::

    decompressRequest(Gzip)          = decodeRequest(Gzip)
    decompressRequest(a, b, c)       = decodeRequest(a) | decodeRequest(b) | decodeRequest(c)
    decompressRequest()              = decodeRequest(Gzip) | decodeRequest(Deflate) | decodeRequest(NoEncoding)

Example
-------

.. includecode:: ../code/docs/directives/EncodingDirectivesExamplesSpec.scala
   :snippet: decodeRequest
