FROM ubuntu:19.04

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y zsh build-essential git cmake vim jq libncurses5-dev libtinfo5 opam mccs

RUN opam init --solver=mccs --disable-sandboxing -y && eval $(opam config env)
RUN opam switch create 4.08.1 -y && eval $(opam config env) && opam update
RUN opam install depext -y && opam depext -i conf-gmp && opam install ocamlbuild ocamlfind batteries stdint zarith yojson fileutils pprint menhir ulex ppx_deriving ppx_deriving_yojson process -y

RUN wget https://github.com/FStarLang/FStar/releases/download/V0.9.7.0-alpha1/fstar_0.9.7.0-alpha1_Linux_x86_64.tar.gz && tar xzfv fstar_0.9.7.0-alpha1_Linux_x86_64.tar.gz -C /usr/local/

RUN eval $(opam config env) && cd /usr/local/fstar && make -C ulib install-fstarlib

COPY zshenv /root/.zshenv
COPY zshrc /root/.zshrc

ENTRYPOINT ["zsh"]
