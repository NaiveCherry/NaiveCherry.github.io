# Node.js对Buffer（缓冲器）的归纳

## 认识Buffer
1. 在 Node.js中，Buffer对象用于以字节序列的形式来表示二进制数据。
2. Node.js 的 API（例如流和文件系统操作）都支持 Buffer，因为与操作系统或其他进程的交互通常总是以二进制数据的形式发生。
3. Buffer 类是JavaScript语言内置的Uint8Array类的子类。
4. 一个 Buffer 的大小在创建时确定，且无法更改。
5. Buffer是一个全局变量，不需要导入。
6. 使用前要先创建好长度。

## 方法

### Buffer.alloc(size[,fill[,encoding]])
```javascript
//创建Buffer对象
var bufalloc = Buffer.alloc(5)  //创建一个长度为5的Buffer对象
console.log(bufalloc)   //<Buffer 00 00 00 00 00>
```

### Buffer.from(string[, encoding])
``` javascript
//创建一个包含string的新Buffer二进制流
var buffrom = Buffer.from('jacky')
console.log(buffrom)  //<Buffer 6a 61 63 6b 79>
var buffrom2 = Buffer.from('jacky','base64')  //字符编码可选
console.log(buffrom2) //<Buffer 8d a7 24>
```

### Buffer.from(array)
```javascript
//使用0 – 255范围内的字节数组 array 来分配一个新的 Buffer
var buffrom3 = Buffer.from([0x6a,0x61,0x63,0x6b,0x79])  //创建一个包含字符串buffer的UTF-8字节的新Buffer,其中0x是头文件，用来告诉计算机是十六进制
console.log(buffrom3.toString())  //jacky
```

### Buffer.isEncoding(encoding)
```javascript
// 如果 encoding 是支持的字符编码的名称，则返回 true，否则返回 false。
console.log(Buffer.isEncoding('utf8'))  //true
console.log(Buffer.isEncoding(''));   //fasle
console.log(Buffer.isEncoding('utf/8'));   //fasle
```

### Buffer.isBuffer(obj)
```javascript
//如果 obj 是一个 Buffer，则返回 true，否则返回 false。
console.log(Buffer.isBuffer(buffer1))
```

## Buffer支持的字符编码

- utf8
> 多字节编码的 Unicode 字符，也是默认的字符编码。
> Unicode万国码
- utf16le
> 多字节编码的 Unicode 字符，与utf8不同，字符串中的每个字符都会使用 2 个或 4 个字节进行编码。 Node.js 仅支持 UTF-16 的小端序变体。
- latin1
> Latin-1代表ISO-8859-1。
### 使用以上方法之一将 Buffer 转换为字符串称为解码；将字符串转换为 Buffer称为编码。

### Node.js 还支持以下两种二进制转文本的编码。将Buffer转换为字符串通常称为编码;而将字符串转换为Buffer 则称为解码。
- base64
> Base64 编码。
- hex
> 将每个字节编码成两个十六进制的字符。
- ascii
> 仅适用于 7 位 ASCII 数据。遗留问题，不推荐使用，纯ASCII码时使用utf8会更好
