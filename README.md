# SPI (Serial Peripheral Interface)

## API

### Includes

```
#include "spi.ceu"
```

### Code Abstractions

#### Spi

Initializes the SPI.

```
code/await Spi (none) -> NEVER;
```

Parameters:

- `none`

Return:

- `NEVER`: never returns

#### SPI_Transaction

Sets up an SPI transaction with the given parameters.

```
code/await SPI_Transaction (var u32 freq, var u8 byte_order, var u8 mode, var int? cs, var int? csn) -> NEVER;
```

Parameters:

- `u32`:  transmission frequency
- `u8`:   byte order (`SPI_LSBFIRST`, `SPI_MSBFIRST`)
- `u8`:   mode of operation (`SPI_MODE0`, `SPI_MODE1`, `SPI_MODE2`, `SPI_MODE3`)
- `int?`: chip select `cs`  pin (active `high`)
- `int?`: chip select `csn` pin (active `low`)

The chip select pins are optional, but at most one may be set.

Return:

- `NEVER`: never returns

SPI transactions cannot be concurrent and must be serialized accordingly.

#### SPI_Transfer

Transmits and receives a byte.

```
code/await SPI_Transfer (var byte? value) -> byte;
```

Parameters:

- `byte?`: value to transmit to the peripheral (default: *don't care*)

Return:

- `byte`: value received from the peripheral

Transfers must always be enclosed in [transactions](#spi_transaction).

### Examples

`TODO`
