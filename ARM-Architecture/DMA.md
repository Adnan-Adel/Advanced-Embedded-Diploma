# Direct Memory Access

## in microcontroller to move data from a place to another, you need to be **MASTER** for the bus (like CPU).

## ex, after the ADC finishes it's operation, we need to move data from ADC register to memory (SRAM):
![[fig1.png]]

## SO, can we move it directly from ADC to memory, and CPU may be doing another thing?
## To do so, we need something also to be MASTER to BUS

# DMA is a peripheral and Master to the bus.
#### **Key Benefits of DMA:**

1. **CPU Offloading**: The CPU can perform other tasks while the DMA controller handles data transfer.
2. **Faster Data Transfer**: DMA allows peripherals to transfer large amounts of data directly to memory, reducing the need for CPU intervention and speeding up operations.
3. **Efficient I/O Operations**: Commonly used for I/O devices like ADC (Analog-to-Digital Converters), UART, SPI, and more, especially when dealing with high-throughput data.
![[fig2.png]]
## Steps to follow while using DMA
1. Identify which DMA controller to use
2. Initialize DMA
3. Trigger DMA (Automatic trigger or Manual trigger)
4. Wait for transfer complete (poll or get callback from DMA Interrupt)


## ex, DMA with UART
1. there is an interrupt line between UART and DMA
2. So, we can configure the UART to trigger it's interrupt after each byte to the DMA
3. and DMA will move it from Data Register to the SRAM
4. and after completion of moving all the bytes we specified while configuring the DMA, the DMA will trigger an interrupt to the CPU.

![[fig3.png]]


#### **Example: DMA in UART Communication**

Consider using DMA for UART communication where large amounts of data need to be transferred between the UART peripheral and memory. The process typically involves the following steps:

1. **Enable UART Peripheral and DMA Controller**.
2. **Configure UART to DMA Mode**: Link UART’s receive (RX) or transmit (TX) buffer to a specific memory location.
3. **Set DMA Parameters**: Choose the DMA channel, set the source (UART RX/TX buffer), and the destination (memory buffer).
4. **Start Data Transfer**: The DMA will transfer data from UART to memory (or vice versa) when UART receives/transmits data.
5. **Completion Interrupt**: Upon completion, DMA triggers an interrupt to signal the CPU that data transfer is done.
![[fig4.png]]

# DMA Controller
[[DMA Controller]]