# LZ4 extension for PHP supporting Block and Frame format

> [!NOTE]
> The pull request to add LZ4 Frame format support to [kjdev/lz4](https://github.com/kjdev/php-ext-lz4/pull/38) has been merged, such that it supports the LZ4 Frame format since version 0.6.0.
> Therefore and because this repository does not support compression levels, this repository is obsolete.

This extension adds support for the [LZ4 compression algorithm](https://github.com/lz4/lz4).

Unlike [kjdev/lz4](https://github.com/kjdev/php-ext-lz4), this extension...

- is based on [lz4_flex](https://github.com/pseitz/lz4_flex) rather than [Cyan4973's LZ4](https://github.com/lz4/lz4)
- supports the LZ4 Frame format, which adds checksums, magic bytes etc.
- does not (yet) support compression levels, since lz4_flex does not

## Install

It is recommended to install this extension via PIE:

```shell
pie install nerou/lz4frame
```

## Usage

Have a look at the [stubs file](lz4frame.stubs.php) to see the API.

If you are wondering what the block vs. frame formats are, have a look at [Block Format](https://github.com/lz4/lz4/blob/dev/doc/lz4_Block_format.md) and [Frame Format](https://github.com/lz4/lz4/blob/dev/doc/lz4_Frame_format.md).
Short version: While the Block format is just the compressed data in a more or less raw variant, the Frame format adds a header and footer around it, which contain magic bytes, checksums, length information etc.
Therefore, the Frame format is much easier to recognize as being LZ4 compressed data compared to the Block format and you get better integrity due to the (optional) checksums.

## License

This project is licensed under the [MIT license](LICENSE.md).
