# Intro

- A collection of key/value pairs where the key can only exist once in the collection
- Examples:
  - HTTP headers
    - Request URL
    - Response Body
    - Browser version
    - Referrer
  - Application configs
  - Environment Variables
  - Key/Value database

# HTTP headers

- The header name and value become the key and value in the associative array

```javascript
HttpHeader headers;
headers["content-length"] = "8056";
headers["content-type"] = "image/png";
```

# Complexity

- An associative array container that provides `O(1) insert, delete and search` operations.

# Hash table
```csharp
class HashTableNodePair<TKey,TValue>{
  
  public HashTableNodePair(TKey key, TValue value)
  {
    Key = key;
    Value = value;
  }
  public TKey Key {get;set;}
  public TValue Value {get;set;}
}
```

# Hash Function

- A function that maps data of arbitrary size to data of a fixed size.
- Examples:
  - Verifying downloaded data
  - Storing passwords in a database
  - Hash tables key lookup

# Stability

- A hash function always generates the same output given the same input

- Stable

  ```csharp

  public int StableHash(string input)
  {
  int result = 0;
  foreach(byte ascii in input)
  {
  result += ascii;
  }
  return result;
  }
  ```

- Unstable

  ```csharp
  public int UnstableHash(string input)
  {
  int result = DateTime.Now.Second;
  foreach(byte ascii in input)
  {
  result += ascii;
  }
  return result;
  }
  ```

- Examples
- Stable

  ```
  StableHash("foo");
  StableHash("foo");
  StableHash("foo");
  324
  324
  324
  ```

- Unstable

  ```
  UnstableHash("foo");
  UnstableHash("foo");
  UnstableHash("foo");
  1449447443
  1449447444
  1449447445
  ```

# Uniformity

- A hash algorithm should distribute its resulting hash value uniformly throughout the output space.
- (More) Uniform

```csharp
public uint SDBMHash(string input)
{
uint hash = 0;
foreach (byte ascii in input)
{
hash = hash * 65599 + ascii;
}
return hash;
}
```

- Non-uniform

```csharp
public int StableHash(string input)
{
int result = 0;
foreach(byte ascii in input)
{
result += ascii;
}
return result;
}
```

- (More) Uniform

```
SDBMHash(”foo");
SDBMHash(”oof");
SDBMHash(”ofo");
849955110
924308646
923718264
```

- Non-uniform

```
StableHash("foo");
StableHash(”oof");
StableHash(”ofo");
324
324
324
```

# Security

- A secure hashing algorithm cannot be inverted (the input derived from the output hash).

```
Username Password Hash (sdbm)
evelyn    3471203675
brian     969889485
will      1978836480
```

```
Password Hash
aaaaaaaa 3834880256
aaaaaaab 3834880257
aaaaaaac 3834880258
aaaaaaad 3834880259
… …
zzzzzzzz 528284160
```

```
Hash        Match       Actual
3471203675  aagkDhA4    password
969889485   aac0xWRs    football
1978836480  aaabhqCy    jedi
```

- Output size: 32, 64, 128, 256, 512

  - 2^32 (4294967296)

  ```
  Checks/sec      Time
  1000            49 Days
  10,000          4.9 Days
  100,000         12 hours
  1,000,000       1 hour
  10,000,000      7 minutes
  100,000,000     42 seconds
  1,000,000,000   4 seconds
  ```

  - 2^512 (1.340781e+154)

  ```
  Checks/sec      Time
  1000            4.25e+143 years
  10,000          4.25e+142 years
  100,000         4.25e+141 years
  1,000,000       4.25e+140 years
  10,000,000      4.25e+139 years
  100,000,000     4.25e+138 years
  1,000,000,000   4.25e+137 years
  ```

# Sample Hash algorithim

## Additive Hash

Pro: Stable, fast
Cons: Poor Uniformity and Security

```
f    o   o
102 111 111
102 213 324
```

## Folding hash

- Pro: Stable, fast , better uniformity
- Cons: Poor security

```
l o r e    m i p      s u m      d o l o     r
1701998444 1885937773 544044403  1869377380  114
1701998444 -707031079 -162986676 1706390704  1706390818
```

## Dbj2 Hash

```csharp
public ulong Dbj2Hash(string input)
{
  ulong hash = 5381;
  foreach(byte c in input)
  {
  hash = hash * 33 + c;
  }
  return hash;
}
```

```
f      o       o
177675 5863386 193491849
```
## Hash Function Comparison
```
Name      Output Size Stable Uniform Secure
Additive      32        YES   NO      NO
Folding       32        YES   YES     NO
Dbj2          64        YES   YES     NO
MD5           128       YES   YES     NO*
SHA-1         160       YES   YES     NO*
SHA-2         224/384   YES   YES     NO*
SHA-2         256-512   YES   YES     YES
```