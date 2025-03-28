# Lessons learned
- RNN (LSTM and generic RNN, probably GRU as well) is not well-suited for sequences with 10,000s of steps.
- Using a stacked LSTM along with a bigger sequence length resulted in the loss converging faster to what seems to be the average value across sequence values, but did not solve the following problem below...
- float64 Tensors just hang there...
- Weird bug encountered where the output of the RNN/LSTM was always the same independently of the batch. I suspect that some form of exploding/vanishing gradient has occurred.
- Training on CPU actually still works for sequence length of 1000, hidden_size = 50, and a basic RNN/LSTM followed by FC layer at the last output.
- Importance of checkpointing. 
- Oh, and read the params, input, and output types at https://pytorch.org/docs/stable/generated/torch.nn.LSTM.html
![image](https://github.com/user-attachments/assets/36d3ec7b-cb92-4c61-8321-1c4c63484ac8)
![image](https://github.com/user-attachments/assets/16776c1c-fd69-4577-98e5-8d7f44d39518)
