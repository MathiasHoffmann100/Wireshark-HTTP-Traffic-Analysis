# Wireshark-HTTP-Traffic-Analysis
This project demonstrates the use of Wireshark to analyze HTTP traffic, focusing on identifying errors, understanding client-server interactions, improving network performance, and detecting potential threats using pre-captured traffic containing vulnerabilities.

Analyzing HTTP traffic with Wireshark is a fundamental skill for understanding client-server communication. It allows professionals to identify errors, diagnose performance issues, and detect potential security risks. By interpreting HTTP requests and responses, Wireshark provides clear visibility into how applications interact over the network, making it a key tool for troubleshooting and maintaining reliable systems.

Once Wireshark is configured in the desired environment, the pre-captured traffic containing the threat should be downloaded (pcaps.zip file attached - Passwd: infected). It is essential to handle this step carefully within an isolated environment, preferably a Linux virtual machine, to prevent any potential risks.

![image](https://github.com/user-attachments/assets/f96cf90b-f385-4f60-aa6d-67f147d8ae90)

Certain Windows infections involve malware or harmful code transmitted via unencrypted HTTP traffic. These malicious objects can be extracted from the pcap file. A demonstration of this process is available in the first pcap file, named Wireshark-tutorial-extracting-objects-from-a-pcap-1-of-5.pcap. Open this file in Wireshark and apply the "http.request" filter to examine the traffic.

![image](https://github.com/user-attachments/assets/14c174de-f9a9-486a-9d8c-182a41bcb477)

By applying the http.request filter, we observe two GET requests directed to the same destination. One request includes a .doc file, while the other contains a .exe file. These objects can be exported for further analysis in detail.

![image](https://github.com/user-attachments/assets/47a4d520-c733-471b-b0b0-77b3d1595e72)

The two files are saved separately. Next, in a Linux environment, the file types should be verified using the command line. The file command identifies the file type, while shasum generates the file hash to ensure the files have not been altered or corrupted.

<b>file<b> [filename]
<b>shasum -a 256<b> [filename]

![image](https://github.com/user-attachments/assets/69937fc6-6e1b-455b-a064-2154f64373b9)

As we now have the hashes, we can check them with VirtusTotal to confirm if the files are in fact detected as malware.

![image](https://github.com/user-attachments/assets/8363e401-640f-4e47-8788-2b3a02ab6678)

![image](https://github.com/user-attachments/assets/64f7ef1a-7efb-449b-9a55-ee60d6ec06a6)

This approach allows us to confirm with certainty that the file is indeed infected, which is crucial for forensic investigations into attacks. Additionally, we can analyze the second file from the pcap, which contains traffic associated with a phishing attempt. This traffic shows an attempt to submit login credentials on a fraudulent PayPal login page. The most effective way to analyze this is by extracting the HTML through HTTP Export, which enables us to retrieve the initial HTML page for examination.

![image](https://github.com/user-attachments/assets/f692cfb6-ba5b-49e5-84e2-e6b039a71129)
![image](https://github.com/user-attachments/assets/22565e2a-1c07-4bac-a39b-847647888014)
