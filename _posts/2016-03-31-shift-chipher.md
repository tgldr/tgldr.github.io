---
layout:     post
title:      Shift Cipher
date:       2016-03-31 09:13:17
summary:    Shift Cipher аргыг Java дээр хийснээ орууллаа. Мөн л хичээл дээр хийх даалгавар байлаа.
categories: Coding Java
---

Encrypt
{% highlight java linenos %}
	package nuutslal;

	import javax.swing.JOptionPane;

	/**
	*
	* @author Tuguldur
	*/
	public class Nuutslal {

		public static void main(String[] args) {
			String s = JOptionPane.showInputDialog(“Утга оруулна уу”);
			String l = JOptionPane.showInputDialog(“Хэдээр гүйлгэх вэ?”);
			String k = “”;
			int m = Integer.parseInt(l);
			for(int i = 0; i < s.length(); i++) {
				char c = (char)(s.charAt(i));
				if (c >= ‘A’ && c <= ‘Z’) {
					k += (char)((c – ‘A’ + m) % 26 + ‘A’);
				} else if (c >= ‘a’ && c <= ‘z’) {
					k += (char)((c – ‘a’ + m) % 26 + ‘a’);
				} else {
					k += c;
				}
			}
			System.out.print(k);
		}

	}
{% endhighlight %}

Decrypt

```java
package nuutslal;

import javax.swing.JOptionPane;

/**
*
* @author Tuguldur
*/
public class Shift_decrypt {
	public static void main(String[] args) {
		String s = JOptionPane.showInputDialog(“Утга оруулна уу”);
		String l = JOptionPane.showInputDialog(“Хэдээр гүйлгэх вэ?”);
		String k = “”;
		int m = Integer.parseInt(l);
		for(int i = 0; i < s.length(); i++) {
			char c = (char)(s.charAt(i));
			if (c >= ‘A’ && c <= ‘Z’) {
				k += (char)((c + ‘A’ – m) % 26 + ‘A’);
			} else if (c >= ‘a’ && c <= ‘z’) {
				if(c – m < 97){
					k += (char)(c-‘a’+’z’-m+1);
				}else {
					k += (char)(c-m);
				}
			} else {
				k += c;
			}
		}
		System.out.print(k);
	}
}
```