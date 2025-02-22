package com.mycompany.adapter;


interface UsbCCharger {
    void chargeWithUsbC();
}

class MicroUsbCharger {
    void chargeWithMicroUsb() {
        System.out.println("Cargando con Micro-USB...");
    }
}

class MicroUsbToUsbCAdapter implements UsbCCharger {
    private final MicroUsbCharger microUsbCharger;

    public MicroUsbToUsbCAdapter(MicroUsbCharger microUsbCharger) {
        this.microUsbCharger = microUsbCharger;
    }

    @Override
    public void chargeWithUsbC() {
        System.out.println("Adaptador en uso: convirtiendo de Micro-USB a USB-C.");
        microUsbCharger.chargeWithMicroUsb();
    }
}

public class ADAPTER {

    public static void main(String[] args) {
        MicroUsbCharger oldCharger = new MicroUsbCharger();
        UsbCCharger adaptedCharger = new MicroUsbToUsbCAdapter(oldCharger);

        adaptedCharger.chargeWithUsbC(); // Se adapta el Micro-USB al USB-C
    }
}
