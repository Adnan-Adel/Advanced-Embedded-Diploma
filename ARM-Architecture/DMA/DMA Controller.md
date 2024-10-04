![[fig5.png]]

## DMA Controller provides 3 AHB Ports : 2 Master ports and 1 Slave Port
1. Memory Port
2. Peripheral Port
3. Programming Port : which is a **Slave Port** used for being programmed by CPU

## DMA Streams
### path to move data inside DMA Controller (each of 8 streams provide a **unidirectional** transfer link between source & destination)

## Each Stream can be configured to perform 
1. memory to peripheral
2. peripheral to memory
3. memory to memory

# peripheral to memory example
![[fig6.png]]

### 1. Peripheral will request DMA (Report Receiving Data)
### 2. each stream is assigned some peripherals, so spi for example may be assigned STREAM2 and STREAM3 
### 3. DMA moves data from peripheral to memory on stream3

# and memory to peripheral is the same


# Memory to Memory:
## ST Considers Memory-to-Memory data transfer, a special case of Peripheral-to-Memory
![[fig7.png]]

# transferring data must be from peripheral port to memory port.


# Streams and Channels
## DMA has 8 Streams each one can take one out of 8 possible Channels.
![[fig8.png]]

### Each stream is associated with a DMA request that can be selected out of 8 possible channel requests.
### The selection is controlled by the CHSEL[2:0] bits in the DMA_SxCR register.

## The 8 requests from the peripherals (such as TIM, ADC, SPI, I2C) are independently connected to each channel and their connection depends on the product implementation.
![[fig9.png]]