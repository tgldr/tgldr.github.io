---
layout:     post
title:      One Time pad cipher
date:       2016-03-30 11:21:29
summary:    Хичээл дээр Cryptography-ийн One time pad cipher аргыг java дээр хий гэсэн даалгавараа хийснээ орууллаа.
categories: Coding Java
---

Encrypt

```java
package nuutslal;

import java.util.Scanner;

/**
*
* @author Tuguldur
*/
public class One_time_pad_enc {

	public static void main(String[] args) {

		Scanner sc = new Scanner(System.in);
		System.out.print("Нууцлах текст оруул: ");
		String sen = sc.nextLine();
		System.out.print("Түлхүүр үгээ оруул: ");
		String key = sc.nextLine();
		char[] lower = new char[26];
		char[] upper = new char[26];
		int m;

		for(int i=0; i< 26; i++){
			lower[i] = (char) (97+i);
			upper[i] = (char) (65+i);
		}

		System.out.print("Нууцлагдсан: ");

		if( sen.length() == key.length() ) {
			for(int i = 0; i < sen.length(); i++) {
				char c = (char)(sen.charAt(i));
				char l = (char)(key.charAt(i));

				if( 'a' <= c && c <= 'z' ) {
					c = (char) (c – 'a');
					l = (char) (l – 'a');
					m = (c+l)%26;
					System.out.print(lower[m]);
				}else if( 'A' <= c && c <='Z' ) {
					c = (char) (c – 'A');
					l = (char) (l – 'A');
					m = (c+l)%26;
					System.out.print(upper[m]);
				}
			}
		}else {
			System.out.print("Нууцлах текст, түлхүүр 2-ийн урт таарахгүй байна.");
		}

		System.out.println();
	}

}
```

Decrypt

```java
package nuutslal;

import java.util.Scanner;

/**
*
* @author Tuguldur
*/
public class One_time_pad_dec {

	public static void main(String[] args) {

		Scanner sc = new Scanner(System.in);
		System.out.print("Нууцлагдсан текст оруул: ");
		String sen = sc.nextLine();
		System.out.print("Түлхүүр үгээ оруул: ");
		String key = sc.nextLine();
		char[] lower = new char[26];
		char[] upper = new char[26];
		int m;

		for(int i=0; i< 26; i++){
			lower[i] = (char) (97+i);
			upper[i] = (char) (65+i);
		}
		System.out.print("Жинхэнэ текст: ");

		if( sen.length() == key.length() ) {
			for(int i = 0; i < sen.length(); i++) {
				char c = (char)(sen.charAt(i));
				char l = (char)(key.charAt(i));

				if( 'a' <= c && c <= 'z' ) {
					c = (char) (c – 'a');
					l = (char) (l – 'a');
					m =(c-l)%26;
					if( m < 0 ) {
						m = m + 26;
					}
					
					System.out.print(lower[m]);
				}else if( 'A' <= c && c <='Z' ) {
					c = (char) (c – 'A');
					l = (char) (l – 'A');
					m = (c-l)%26;
					if( m < 0 ) {
						m = m + 26;
					}
					System.out.print(upper[m]);
				}
			}
		}else {
			System.out.print("Нууцлагдсан текст, түлхүүр 2-ийн урт таарахгүй байна.");
		}

		System.out.println();
	}

}
```