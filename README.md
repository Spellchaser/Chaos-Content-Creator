# Chaos Content Creator

`yafg` stands for `yet another fuzz generator`

## Why?

What makes this different from the numerous fuzzing libraries already published?

This library was designed to poison attack central APIs and shared resources in order to force and enforce a client's ability to handle an adverse environment.
A concrete example of this scenario is posting a message partially schema compliant to a message queue like kafka and expecting client code to gracefully handle missing fields.

Unlike the [Google OSS-Fuzz](https://github.com/google/oss-fuzz) approach which tackles fuzz issues at the CI/CD project level, yafg should publish fuzz messages (maybe just in stage) to a central kafka topic or mock invalid responses for a discoverable HTTP api. This adds another layer of protection at a distributed level. While OSS-Fuzz will provide targeted, in-depth spot checks, yafg attempts to raise the quality floor of all services using a distributed system.
> #TODO: insert graphic of floor vulnerability vs spot fixes with CI
`yafg` is meant to be used in conjunction with some chaos engineering framework. The generated messages should be used to poison test systems and provides a standardized config around primitive and more complex generated types.


#### Stated in a different lens:

A common service provider may say
> "You must be able to handle a corrupt message if you intend to use our service."

An SRE team may say
> "If you read and write authenticated messages on our kafka topics, you must be able to gracefully handle a corrupt, tombstone, or partially formatted message. If you do not use a provided central wrapper library that handles encryption and decryption, if your implementation does not work, it will fail in stage."


#### Fuzz/Fuzzing:

See [OSS-Fuzz](https://github.com/google/oss-fuzz)


# CCC generic fuzz generation framework
