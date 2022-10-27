# SHA-256 Cryptographic Hash Algorithm for Bitcoin Miner
Description of SHA256: https://eips.ethereum.org/assets/eip-2680/sha256-384-512.pdf
- An n-bit hash is a map from arbitrary length messages to n-bit hash values. 
- An n-bit cryptographic hash is an n-bit hash which is one-way and collision-resistant. Such functions are important cryptographic primitives used for such things as digital signatures and password protection.
- Current popular hashes produce hash values of length n = 128 (MD4 and MD5) and n = 160 (SHA-1), and, therefore can provide no more than 64 or 80 bits of
security, respectively, against collision attacks. Since the goal of the new Advanced Encryption Standard (AES) is to offer, at its three cryptovariable sizes, 128, 192, and 256 bits of security, there is a need for companion hash algorithms which provide similar levels of enhanced security. 
- SHA-256 is a 256-bit hash that provides 128 bits of security against collision attacks.

## Overview
- The Bitcoin miner and SHA256 hashing algorithm were written from scratch in C++.
- SHA-256 operates in the manner of MD4, MD5, and SHA-1: The message to be hashed is first
  - (1) padded with its length in such a way that the result is a multiple of 512 bits long, and then
  - (2) parsed into 512-bit message blocks <i>M</i><sup>1</sup>, <i>M</i><sup>2</sup>,..., <i>M</i><sup><i>N</i></sup></i>
  - The message blocks are processed one at a time: Beginning with a fixed initial hash value <i>H</i>^0, sequentially compute: 
    - <i>H</i><sup><i>i</i></sup> = <i>H</i><sup>(<i>i</i>-1)</sup> + <i>C</i><sub><i>M</i><sup><i>i</i></sup></sub> (<i>H</i><sup>(<i>i</i>-1)</sup>)
  - where C is the SHA-256 compression function and + means word-wise mod 2<sup>32</sup> addition. <i>H</i><sup>(<i>N</i>)</sup> is the hash of of <i>M</i>

## Function
The SHA-256 compression function operates on a 512-bit message block and a 256-bit intermediate hash value. It is a 256-bit block cypher algorithm that encrypts the intermediate hash value using the message block as the key. Hence there are two main components to describe: (1) the SHA-256 compression function and (2) the SHA-256 message schedule.

<img src="https://github.com/issacjohannli/sha-256-hash-algorithm-bitcoin-miner/blob/main/diagrams/sha-256-compression-function.png">

## Diagrams
The SHA-256 compression function is shown below, where the square tile symbols denote mod 2<sup>32</sup> addition.

Figure 1: <i>j</i><sup>th</sup> internal step of the SHA-256 compression function <i>C</i>.

## Sample Hash Computations
The result of hashing the 24-bit message "abc". After padding, the message becomes (in hexadecimal):\
61626380 00000000 00000000 00000000 00000000 00000000 00000000 00000000\
00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000018;\
and the hash value is\
ba7816bf 8f01cfea 414140de 5dae2223 b00361a3 96177a9c b410ff61 f20015ad.
