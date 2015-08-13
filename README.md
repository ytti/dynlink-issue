[ytti@ytti.fi ~/usr/git/dynlink-issue]% find
```
.
./src
./src/foo.rs
./Cargo.toml
```

[ytti@ytti.fi ~/usr/git/dynlink-issue]% cat src/foo.rs
```rust
extern crate pnet;
fn main() {}
```

[ytti@ytti.fi ~/usr/git/dynlink-issue]% cat Cargo.toml
```toml
[package]
name    = "foo"
version = "0.0.0"
authors = [ "saku@ytti.fi" ]

[[bin]]
name = "foo"

[dependencies.pnet]
git = "https://github.com/libpnet/libpnet.git"
```

[ytti@ytti.fi ~/usr/git/dynlink-issue]% cargo buil
```
    Updating git repository `https://github.com/libpnet/libpnet.git`
    Updating registry `https://github.com/rust-lang/crates.io-index`
   Compiling pnet v0.1.0 (https://github.com/libpnet/libpnet.git#31fefb3a)
   Compiling libc v0.1.8
   Compiling regex-syntax v0.2.1
   Compiling memchr v0.1.3
   Compiling aho-corasick v0.3.0
   Compiling regex v0.1.41
   Compiling pnet_macros v0.1.0 (https://github.com/libpnet/libpnet.git#31fefb3a)
   Compiling foo v0.0.0 (file:///home/ytti/usr/git/dynlink-issue)
```

[ytti@ytti.fi ~/usr/git/dynlink-issue]% ldd target/debug/foo
```
	linux-vdso.so.1 (0x00007fff88bd7000)
	libstd-35017696.so => /usr/local/lib/libstd-35017696.so (0x00007f3f6ba4d000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f3f6b6a4000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f3f6b49f000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f3f6b282000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f3f6b07a000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f3f6ae63000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f3f6c26e000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f3f6ab62000)
```
[ytti@ytti.fi ~/usr/git/dynlink-issue]%
