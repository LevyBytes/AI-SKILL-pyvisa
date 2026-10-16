# VISA shell termchar settings and close
Context: PyVISA introduction; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](events-and-visa-shell-index.md) / [VISA shell launch, help, discovery, open and timeout](visa-shell-session-commands.md) / [VISA shell complete resource-attribute output](visa-shell-resource-attribute-output.md)

The termchar command simplifies working with VI_ATTR_TERMCHAR and VI_ATTR_TERMCHAR_EN. Supplying one character applies that character to both read and write termination. Supplying two characters configures the read and write termination characters separately.

To setup termchar to `\r` (CR, ASCII code 13):

```text
(open) termchar CR
Done

```

To read what termchar is defined:

```text
(open) termchar
Termchar read: CR write: CR

```

To setup read termchar to `\n` and write termchar to `\r\n`:

```text
(open) termchar LF CRLF
Done

```

Accepted termchar settings are CR (`\r`), LF (`\n`), CRLF (`\r\n`), NUL (`\0`), and None. Use None when termchar should be disabled.

Finally, you can close the device:

```text
(open) close

```

