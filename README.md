# Huffman Substring Compression

This project consists of a text compression method using a combination of the Huffman algorithm and substring mechanics. This method is able to compress text files better using less memory than traditional compression algorithms such as .zip, .gzip, .bzip2, etc. However, it is much slower due to the nature of the file. However, it is much slower due to the nature of the Huffman algorithm.


## Method of operation

<img src='https://brilliant-staff-media.s3-us-west-2.amazonaws.com/tiffany-wang/VEIWKBhSSc.png' style='height:200px'></img>

The Huffman algorithm is a lossless data compression algorithm that uses a binary tree to encode data. The tree is built from a table of character frequencies in the text to be compressed. Each character is encoded with a unique binary code determined by the position of its leaves in the tree. The most frequent characters are encoded with shorter binary codes, which allows a more efficient compression.

<img src='https://docs.fauna.com/fauna/current/api/_images/SubString.svg' style='width:600px'></img>

Substring mechanics, on the other hand, involves identifying repetitive substrings in the text to be compressed and replacing them with unique symbols. These symbols can then be encoded using the Huffman algorithm for further compression.

## The Huffman Substring Compression method

The Huffman Substring Compression method combines these two techniques for more efficient compression of text files. First, the generate_substrings(text: str) function is used to identify all repeating substrings in the text to be compressed. Then, these substrings are replaced with unique symbols, which in turn are encoded using the Huffman algorithm. Finally, the encoded text is saved in a compressed file.

#### Example :
```py
>>> compressed, dic, huffman_tree = hsc_compress(text[:200], 2)
>>> print(dic)
[' co', ' con', ' er', ' era', ' erat', ', c', ', co', 'at.', 'at. ', 'cin', 'con', 'era', 'erat', 'is ', 'rat', 't, ', 't, c', 't, co', 't. ']
```

## Complexity of the method

The complexity of the Huffman Substring Compression method is in $O(n^2)$, where n is the length of the text to be compressed. This complexity is due to the generate_substrings(text: str) function, which must traverse all possible substrings in the text. However, this complexity can be considerably reduced by limiting the minimum length of the substrings to be replaced by single symbols.

The reason why this compression method can be more efficient than traditional compression algorithms such as .zip, .gzip, .bzip2, etc. is due to the use of the Huffman algorithm combined with substring mechanics. The Huffman algorithm is known for its ability to efficiently compress data without loss, while substring mechanics identifies repetitive substrings and replaces them with unique symbols, which can be encoded more efficiently by the Huffman algorithm.

However, this method is also much slower due to the nature of the Huffman algorithm, which requires the construction of a binary tree to encode the data. In addition, the generate_substrings(text: str) function can take a long time since it checks all possible string possibilities.

However, the overall complexity of the compression algorithm also depends on the complexity of the Huffman compression method. The Huffman complexity is $O(n\log{n})$, where n is the number of symbols in the string to be compressed. This is due to the construction of the Huffman tree, which requires the symbols to be sorted according to their frequency of occurrence.

In practice, the overall complexity of the Huffman Substring compression method is therefore $O(n^2\log{n})$, making it much slower than modern compression methods like Brotli.

However, despite its slowness, the Huffman Substring compression method can provide better compression than faster methods like ZIP or GZIP, especially for file types that contain repeating patterns or medium-length substrings.


## Choice of the value of $l$

<img src='https://raw.githubusercontent.com/ImGalaad/HuffmanSubstringCompression/main/l_plotting.png' style='height:400px'></img>

In the HSC method, the value of $l$ is used to determine the minimum length of a substring that can be compressed. The larger $l$ is, the more efficient the compression, but it also increases the computation time.

The recommended formula for determining $l$ is $l = \lceil\sqrt{\frac{len - 1}{100} + 1}\rceil$, where len is the length of the input string. This formula is based on experiments conducted by the authors of the method and yields optimal compression results for most texts.

However, it is important to note that the choice of $l$ depends on the nature of the input string. For some texts, a value larger or smaller than that given by the formula may give better results. It is therefore recommended to experiment with different $l$ values for each text to be compressed.
