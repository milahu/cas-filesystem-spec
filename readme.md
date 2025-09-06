# cas-filesystem-spec

`/cas/{hashtype}/{hash}/{filename}`

a filesystem specification for a generic [Content Addressed Storage](https://en.wikipedia.org/wiki/Content-addressable_storage)

## spec

### cas directories

the cas filesystem consists of multiple cas directories

```
/cas
/home/someuser/cas
/tmp/cas
/media/somelabel/cas
/run/media/someuser/somelabel/cas
/mnt/somemointpoint/cas
C:/cas
D:/cas
```

### hashtype directories

each of these cas directories has multiple subdirectories,
representing different hash types.
we call them "hashtype directories"

```
/cas/md5
/cas/sha1
/cas/btih
/cas/git
/cas/sha256
/cas/size
/cas/todo
```

exception: `size` is the file size in bytes

exception: `todo` is a directory for files with unknown hash, but the hash will be known in the future,
so the files can be moved to other hashtype-directories

## related

- [wikipedia: Content-addressable storage](https://en.wikipedia.org/wiki/Content-addressable_storage)
- [github.com/milahu/cas_torrent](https://github.com/milahu/cas_torrent) - a bittorrent client with content-addressed storage
  - [4.2.5 overwrites files if file names are the same qBittorrent#12842](https://github.com/qbittorrent/qBittorrent/issues/12842)
- [Nix sha256 is bug not feature. solution: a global /cas filesystem](https://discourse.nixos.org/t/nix-sha256-is-bug-not-feature-solution-a-global-cas-filesystem/15791) -
  problem: source files and build files are stored in the same CAS format, ...
  which is a LOSSY transformation, since /nix/store is messing with file permissions.
  solution: store source files in their original format,
  to get a LOSSLESS local copy of the source files
- [github.com/perkeep/perkeep](https://github.com/perkeep/perkeep) - Perkeep is your personal storage system for life: a way of storing, syncing, sharing, modelling and backing up content
- [github.com/okhosting/awesome-storage](https://github.com/okhosting/awesome-storage)
- [github topic: content-addressable-storage](https://github.com/topics/content-addressable-storage)
- [github topic: content-addressed-storage](https://github.com/topics/content-addressed-storage)
- [Magnet-URI Webseeding libtorrent#7960](https://github.com/arvidn/libtorrent/pull/7960) - add `cas` parameter to magnet links
