# Setting Up Your Assembly Language Environment

## Install an Assembler

You need an assembler to convert assembly code into machine code. Popular assemblers include:

- **NASM (Netwide Assembler)**: [NASM Website](https://www.nasm.us/)
- **MASM (Microsoft Macro Assembler)**: [MASM Documentation](https://docs.microsoft.com/en-us/cpp/assembler/masm/)

## Set Up Your Environment

1. **Download and Install the Assembler**:
    - **NASM**: Visit the [NASM Website](https://www.nasm.us/) and follow the download and installation instructions for your operating system.
    - **MASM**: Refer to the [MASM Documentation](https://docs.microsoft.com/en-us/cpp/assembler/masm/) for installation steps.

2. **Configure Your Development Environment**:
    - **Windows**:
        - Add the assembler's installation directory to your system's PATH environment variable.
        - Example for NASM: 
            1. Open the Start Menu, search for "Environment Variables", and select "Edit the system environment variables".
            2. Click on "Environment Variables".
            3. Under "System variables", find and select the "Path" variable, then click "Edit".
            4. Click "New" and add the path to the NASM installation directory (e.g., `C:\Program Files\NASM`).
            5. Click "OK" to save the changes.
    - **Linux**:
        - Add the assembler's installation directory to your PATH in your shell configuration file (e.g., `.bashrc` or `.zshrc`).
        - Example for NASM:
            ```sh
            echo 'export PATH=$PATH:/path/to/nasm' >> ~/.bashrc
            source ~/.bashrc
            ```
    - **macOS**:
        - Similar to Linux, add the assembler's installation directory to your PATH in your shell configuration file (e.g., `.bash_profile` or `.zshrc`).
        - Example for NASM:
            ```sh
            echo 'export PATH=$PATH:/path/to/nasm' >> ~/.zshrc
            source ~/.zshrc
            ```

3. **Verify Installation**:
    - Open a terminal or command prompt.
    - Run the assembler's version command to verify the installation.
        - For NASM: `nasm -v`
        - For MASM: `ml /?`

## Writing and Compiling Your First Assembly Program

1. **Create a Source File**:
    - Create a new file with a `.asm` extension (e.g., `hello.asm`).
    - Write a simple assembly program. Example for NASM:
        ```asm
        section .data
            msg db 'Hello, World!', 0

        section .text
            global _start

        _start:
            ; Write the message to stdout
            mov eax, 4
            mov ebx, 1
            mov ecx, msg
            mov edx, 13
            int 0x80

            ; Exit the program
            mov eax, 1
            xor ebx, ebx
            int 0x80
        ```

2. **Assemble the Source File**:
    - Open a terminal or command prompt.
    - Navigate to the directory containing your source file.
    - Run the assembler to convert the source file into an object file.
        - For NASM: `nasm -f elf64 hello.asm -o hello.o`
        - For MASM: `ml /c /coff hello.asm`

3. **Link the Object File**:
    - Use a linker to create an executable from the object file.
        - For NASM (using `ld`): `ld -s -o hello hello.o`
        - For MASM (using `link`): `link /subsystem:console hello.obj`

4. **Run the Executable**:
    - Execute the compiled program.
        - On Windows: `hello.exe`
        - On Linux/macOS: `./hello`
