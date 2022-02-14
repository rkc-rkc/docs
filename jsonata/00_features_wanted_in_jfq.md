## Here are a list of features that would be nice to have in jfq

[JFQ](https://github.com/blgm/jfq) is a command line wrapper to the jsonata javascript library

- Allow to pass parameters from command line
  - To keep the query usable in more than one scenario it would help to be able to pass a parameter into the query. Jsonata library has a way of allowing external bindings. JFQ can set up the bindings to the values passed in the parameter
- Allow invoking functions from node
  - Jsonata library allows calling functions defined elsewhere in a library. This can be extremely useful when using JFQ as a glue code. There are some security concerns to be kept in mind. Few that pop up are:
    - Use approved list in config
      - Explicitly disallow eval
      - http client : axios
        - https://attacomsian.com/blog/http-requests-in-nodejs/ 
- Chain a list of transforms
  - Sometimes to achieve a goal it is easier to make a sequence of querries rather than have to compose all the desired outcome in a single query. It would be nice if this is available in Jsonata library. But until then it would be nice to have it in JFQ. JFQ can take a list of querries either on command line or through a list of -q query files
