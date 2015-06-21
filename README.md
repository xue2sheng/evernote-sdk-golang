# Evernote SDK Golang

This project was simple code generated from [Evernote-thrift](https://github.com/evernote/evernote-thrift)-1.25 .

# Simple

See [client_test.go](client/client_test.go)

```golang
c := NewClient(EvernoteKey, EvernoteSecret, SANDBOX)
us, err := c.GetUserStore()
if err != nil {
    t.Fatal(err)
}
url, err := us.GetNoteStoreUrl(EvernoteAuthorToken)
if err != nil {
    t.Fatal(err)
}
if len(url) < 1 {
    t.Fatal("Invalid URL")
}
ns, err := c.GetNoteStoreWithURL(url)
if err != nil {
    t.Fatal(err)
}
note, err := ns.GetDefaultNotebook(EvernoteAuthorToken)
if err != nil {
    t.Fatal(err)
}
if note == nil {
    t.Fatal("Invalid Note")
}
```

# How to generate yourself code

1. Install the newest Thrift. It's a type alias bug of golang generator [THRIFT-2955](https://issues.apache.org/jira/browse/THRIFT-2955).
1. Clone the official evernote-thrift repo `https://github.com/evernote/evernote-thrift`
1. Generator with this command:

    thrift -strict -nowarn --allow-64bit-consts --allow-neg-keys --gen go:package_prefix=github.com/dreampuf/evernote-sdk-golang/ evernote-thrift/src/UserStore.thrift

1. Enjoy!

