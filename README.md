# misra

# Enums

## Wrong Way
```
typedef enum
{
    MCP23S17_IOCON_BANK          = 0x80U,
    MCP23S17_IOCON_MIRROR        = 0x40U,
    MCP23S17_IOCON_SEQOP         = 0x20U,
    MCP23S17_IOCON_DISSLW        = 0x10U,
    MCP23S17_IOCON_HAEN          = 0x08U,
    MCP23S17_IOCON_ODR           = 0x04U,
    MCP23S17_IOCON_INTPOL        = 0x02U,
    MCP23S17_IOCON_UNIMPLEMENTED = 0x01U,
} MCP23S17_IOCON_Val_t;

...

    ASSERT ( IOExpander_MCP23S17_SetConfig ( &s_ioExpander,
                                             (MCP23S17_IOCON_Val_t) (MCP23S17_IOCON_MIRROR
                                             | MCP23S17_IOCON_INTPOL )));
```

Gets the following error

```
note 9030: cannot cast a signed value to an enum type [MISRA 2012 Rule 10.5, advisory]
                                             (MCP23S17_IOCON_Val_t) (MCP23S17_IOCON_MIRROR
                                             ^
note 9027: an enum value is not an appropriate left operand to | [MISRA 2012 Rule 10.1, required]
                                             | MCP23S17_IOCON_INTPOL )));
```

## Right Way

```
typedef uint8_t MCP23S17_IOCON_Val_t;
#define MCP23S17_IOCON_BANK          (( MCP23S17_IOCON_Val_t ) 0x80U)
#define MCP23S17_IOCON_MIRROR        (( MCP23S17_IOCON_Val_t ) 0x40U)
#define MCP23S17_IOCON_SEQOP         (( MCP23S17_IOCON_Val_t ) 0x20U)
#define MCP23S17_IOCON_DISSLW        (( MCP23S17_IOCON_Val_t ) 0x10U)
#define MCP23S17_IOCON_HAEN          (( MCP23S17_IOCON_Val_t ) 0x08U)
#define MCP23S17_IOCON_ODR           (( MCP23S17_IOCON_Val_t ) 0x04U)
#define MCP23S17_IOCON_INTPOL        (( MCP23S17_IOCON_Val_t ) 0x02U)
#define MCP23S17_IOCON_UNIMPLEMENTED (( MCP23S17_IOCON_Val_t ) 0x01U)
```
