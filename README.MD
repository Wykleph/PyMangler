# PyMangler

PyMangler contains a pure-python "encryption" scheme 
that can be used to *obfuscate* and *disguise* data
in situations where strong encryption is not available,
and security is not necessarily top priority.

### Install

    pip install PyMangler

### Setup

The key file that comes with PyMangler will work,
but you should generate a new key by running the 
`keygen.py` file.  You should see the following 
text and a file named `key` will be generated:

    Generating key...
    Key generated.
    Validating key for prosperity...
    Key is valid.  Encryptor working successfully!

A key should never fail, but it's validated anyway.

PyMangler's encryption algorithm was designed to give 
a fairly flat distribution frequency, and repeating 
patterns in pre-encrypted text does not generate 
repeating cipher-text that would give any indication
of a pattern.

    hello hello hello hello hello hello hello hello
    ̬ĮʀÀ
    (ŬǊɢʷMfǱċǚϺ-éȼ˭̕ȿïɐǅƹ{əʺʙΦΑțϾɚɛ͜ǙʡƽǛť
    
    aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
    ΧϬʸΟϫ«͚ǣϱȐ˩ȍ3͜p̚ĺ̒bĘʇɅ͋Ƚďɏ͛ʬƥƏƼʌˢ͊ǝͅ#ȇƄƩŨ϶Ǖ³¾

### Usage

```python
from PyMangler.mangle import Encryptor

# The Encryptor class will generate a key to use
# on instantiation. Save your key file or else
# you won't be able to recover encrypted data.

e = Encryptor()
e.save_key_file(filepath='/Path/To/Key/File')
# once you save a key file you wouldn't want to 
# overwrite it so make sure you create a key
# generator or use the one provided.

# You can load the key file you saved.
e.load_key_file(filepath='/Path/To/Key/File')

# If you don't like PyManglers key contruction 
# methods you can use the make_key method to 
# create your own. Just pass a list of random
# characters and Encryptor will number each 
# character starting from 1.
e.make_key(['d', 'c', 'b', 'e', 'g', 'a', 'f'])

# if you want Encryptor to randomize your
# key for you, use make_randomized_key.
e.make_randomized_key(['a', 'b', 'c', 'd', 'e', 'f', 'g']) 

# Using either make_key or make_randomized_key
# will make Encryptor use your given characters

# Calling Encryptor.save_key_file will save your
# created key to a file that can be loaded later.

```
