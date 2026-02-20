
# Getting Started with RISC-V on GitHub Codespaces

Follow the steps below to set up and run programs in your own Codespace.

---

## Step 1. Open the Repository

Go to:  
[https://github.com/vsdip/vsd-riscv2](https://github.com/vsdip/vsd-riscv2)

---

And Fork it to your Github <br></br>

<br>
<img width="479" height="332" alt="image" src="https://github.com/user-attachments/assets/8b1c63c3-c893-4756-a874-bea8eb3d95e9" />

<br>

## Step 2. Create a Codespace

1. Log in with your GitHub account.
2. Click the green **Code** button.
3. Select **Open with Codespaces** → **New codespace**.
4. Wait while the environment builds. (First time may take 10–15 minutes.)


<img width="1920" height="1008" alt="Screenshot 2026-02-20 184000" src="https://github.com/user-attachments/assets/f83e9c2b-ac18-4688-b7db-4e22c99bcabb" />
<br>
A Window like this will appear. Give it about 15 minutes to Fully get done.
<br>
<img width="1920" height="1008" alt="Screenshot 2026-02-20 191122" src="https://github.com/user-attachments/assets/49f99459-64ab-4b16-a6ea-df54eb2ad43c" />

---

## Step 3. Verify the Setup

In the terminal that opens, type:

```bash
riscv64-unknown-elf-gcc --version
spike --version
iverilog -V
````

You should see version information for each tool.
<br>
<img width="479" height="332" alt="image" src="https://github.com/user-attachments/assets/33c7c07d-06bd-49bd-b449-96b7ed19891f" />
<br>

---

## Step 4. Run Your First Program

1. Go to the `samples` folder.
2. Compile the program:

   ```bash
   riscv64-unknown-elf-gcc -o sum1ton.o sum1ton.c
   ```
3. Run it with Spike:

   ```bash
   spike pk sum1ton.o
   ```

Expected output:

```text
Sum from 1 to 9 is 45
```
<br>

<img width="943" height="297" alt="Screenshot 2026-02-20 191248" src="https://github.com/user-attachments/assets/b6517864-dbb7-48e1-9c37-db6194da149e" />



---

## Step 5. Next Steps

* You can edit and run your own C programs.


<br>
<img width="886" height="302" alt="Screenshot 2026-02-20 191918" src="https://github.com/user-attachments/assets/ef6aeda0-2015-46e9-a6bf-36308b09f3d7" />


---

# Working with GUI Desktop (noVNC) – Advanced

The following steps show how to use a full Linux desktop inside your Codespace and run the same RISC-V programs there.

---

## Step 6. Launch the noVNC Desktop

1. In your Codespace, click the **PORTS** tab.

2. Look for the forwarded port named **noVNC Desktop (6080)**.

3. Click the **Forwarded Address** link.

<img width="983" height="290" alt="Screenshot 2026-02-20 191500" src="https://github.com/user-attachments/assets/d25f44bc-4c16-4c9a-bdc6-ddc38288baf2" />



4. A new browser tab opens with a directory listing. Click **`vnc_lite.html`**.

<img width="960" height="504" alt="image" src="https://github.com/user-attachments/assets/769fe34c-436a-42ea-b9a3-1b8bfaec8637" />

 
5. The Linux desktop appears in your browser.

<img width="1920" height="1080" alt="Screenshot 2026-02-20 191347" src="https://github.com/user-attachments/assets/f66342a0-a38d-4153-a354-0e5a8eab44b5" />


---

## Step 7. Open a Terminal Inside the Desktop

1. Right-click anywhere on the desktop background.
2. Select **Open Terminal Here**.

   ![Open terminal here](images/4.png)

A terminal window will open on the desktop.

---

## Step 8. Navigate to the Sample Programs

In the terminal, go to the workspace and then to the `samples` folder:

```bash
cd /workspaces/vsd-riscv2
cd samples
ls -ltr
```

You should see files like `sum1ton.c`, `1ton_custom.c`, `load.S`, and `Makefile`.

![Samples folder listing](images/5.png)

---

## Step 9. Compile and Run Using Native GCC (x86)

First, compile and run the C program with the standard `gcc` compiler:

```bash
gcc sum1ton.c
./a.out
```

Expected output:

```text
Sum from 1 to 9 is 45
```

![Native GCC run](images/6.png)

---

## Step 10. Compile and Run Using RISC-V GCC and Spike

Now compile the same program for RISC-V and run it on the Spike ISA simulator:

```bash
riscv64-unknown-elf-gcc -o sum1ton.o sum1ton.c
spike pk sum1ton.o
```

You will see the proxy kernel (`pk`) messages and then the program output.

![Spike run](images/7.png)

---

## Step 11. Edit the C Program Using gedit (GUI Editor)

To edit the program using a graphical editor:

```bash
gedit sum1ton.c &
```

This opens `sum1ton.c` in **gedit** on the noVNC desktop.

![gedit editing](images/8.png)

Make changes (for example, change `n = 9;` to another value), save the file, and re-run:

```bash
riscv64-unknown-elf-gcc -o sum1ton.o sum1ton.c
spike pk sum1ton.o
```

---

You have now:

* Launched a full Linux desktop inside GitHub Codespaces
* Compiled and executed a C program with native GCC
* Compiled and executed the same program on a RISC-V target using Spike
* Edited and rebuilt the code using a GUI editor over noVNC

You’re ready to explore more RISC-V and Verilog labs in this Codespace.


