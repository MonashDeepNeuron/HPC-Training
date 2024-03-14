# The HPC Training Book

![Build Status](https://github.com/MonashDeepNeuron/HPC-Training/workflows/CI/badge.svg)

This repository contains the source code for the HPC Training content and challenges for new HPC recruits. This book is available online or can be built locally.

## Building

To build this book you need [mdBook](https://rust-lang.github.io/mdBook/index.html) a tool for creating books with Markdown. mdBook can be installed using Cargo - Rust's package manager.

```sh
cargo install mdbook
```

You can build this book you must clone this repository using Git. You can then build it and even serve it to localhost to view in your browser. The serve command will produce a localhost you can view.

```sh
$ git clone https://github.com/MonashDeepNeuron/HPC-Training.git
$ cd HPC-Training

# Build ...
$ mdbook build

# ... or serve build and serve locally
$ mdbook serve --open
```

## Contributors

- Tyler Swann
- Ankita Gosavi
- Mitchell Mibus
- Nikhil Kannachel
- Jaspar Martin
- Yuki Kume
- Osman Haji
- Duc Thanh Vinh Nguyen

## Code of Conduct, License & Contributing

Refer to the [Code of Conduct](/CODE_OF_CONDUCT.md) and the [License](/LICENSE) for this repository for the expected behavior of contributors and users of the repository. If you have any concerns, open a discussion or contact the appropriate members of Monash DeepNeuron. If you wish to contribute, follow the [contributing guide](/CONTRIBUTING.md).
