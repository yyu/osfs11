Operating System From Scratch
-----------------------------

Step 11: Learn with fun
```````````````````````

Let's make some fun.

Boot from hard disk
'''''''''''''''''''

We've created an FS in the hard disk and there are pretty much stuff in it, but so far we can only boot from a floppy disk.
It's not hard to write a boot sector and a boot loader for a hard drive.
See ``b/`` for details.

Boot from grub
''''''''''''''

We can install the OS in any partition of the hard drive then boot it using grub.

I tried grub 0.97:

1. get grub 0.97 and compile it::

   $ ./configure
   $ make

2. get two files: ``grub-0.97/stage1/stage1`` and ``grub-0.97/stage2/stage2``

3. write ``stage1`` and ``stage2`` to the disk image::

   $ dd if=stage1 of=80m.img bs=1 count=446 conv=notrunc
   $ dd if=stage2 of=80m.img bs=512 seek=1 conv=notrunc

Note that we don't install the whole grub, we just pick up two files.
That's enough.

Now start Bochs, when you see the grub prompt, type these in (note that ``hd0,4`` means the first logical partition)::

   grub> rootnoverify (hd0,4)
   grub> chainloader +1
   grub> boot

Then our OS will boot.

Orange'S in real machine
''''''''''''''''''''''''

We've been running our OS in Bochs for a while.
Have you ever wonder if it works in a real machine?
Well, you can test it!

One day I installed Orange'S in my old PC with an even older 10GB Seagate hard disk.
It works good!

.. image:: http://osfromscratch.org/snapshots/original/%E5%9B%BE11.04%20photo-%E5%9C%A8%E7%9C%9F%E5%AE%9E%E7%9A%84%E6%9C%BA%E5%99%A8%E4%B8%AD%E4%BD%BF%E7%94%A8echo%E5%91%BD%E4%BB%A4.png

.. image:: http://osfromscratch.org/snapshots/original/%E5%9B%BE11.05%20photo-%E5%9C%A8%E7%9C%9F%E5%AE%9E%E7%9A%84%E6%9C%BA%E5%99%A8%E4%B8%AD%E4%BD%BF%E7%94%A8ls%E5%91%BD%E4%BB%A4.png

Have fun
''''''''

I wrote my OS because I was curious.
I had a lot of fun when I saw it grew up.
I hope you have had a lot of fun too when you read, compile and test my code.
If you do, *fork* it and keep having fun, and don't forget to let me know. :)

`‹prev`_

.. _`‹prev`: https://github.com/yyu/osfs10
