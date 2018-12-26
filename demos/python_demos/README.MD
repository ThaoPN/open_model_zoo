
## Multiple NCS2 Devices Inference Demo 

This is a very simple demo to show how to use multiple threads to use multiple ncs2 device to do inference in parallel. 
The key idea is to create multiple `IENetwork` instances each of which is mapped to one ncs2 device.

In this demo `multiple_device_ncs2_async.py`, multiple threads are used, and each worker thread owns one `NcsClassifier` instance. 
The `Scheduler` class create one thread for image pre-processing as producer, and consumer threads  take item from queue and do inference.

### To run the demo

* Prepare the network and got IR, for example `squeezenet1.1.xml`
* Run the demo. `num_device` specify the number of ncs2 devices. Error will be raised if it exceeds the actual number of ncs2 devices 
plugged on the host machine 
```
python3 multiple_device_ncs2_async.py --imgpath /path/to/images --num_device 2 --model /path/to/model/xml --input_shape [1,3,227,227]
```

### Reference
https://software.intel.com/en-us/articles/transitioning-from-intel-movidius-neural-compute-sdk-to-openvino-toolkit


