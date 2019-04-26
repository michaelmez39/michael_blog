+++
title="Paasio"
description="The Paasio exercism challenge is to make a wrapper to track the amount of reads and writes for a Read and Write type."
date = 2019-04-26
+++
# Paasio
## Sample Page
With some *stuff*


```rust

pub struct ReadStats<R>{
    reader: R,
    reads: usize,
    through: usize
}

impl<R: Read> ReadStats<R> {
    pub fn new(wrapped: R) -> ReadStats<R> {
        ReadStats {
            reader: wrapped,
            reads: 0,
            through: 0
        }
    }

    pub fn get_ref(&self) -> &R {
        &self.reader
    }

    pub fn bytes_through(&self) -> usize {
        self.through
    }

    pub fn reads(&self) -> usize {
        self.reads
    }
}

impl<R: Read> Read for ReadStats<R> {
    fn read(&mut self, buf: &mut [u8]) -> Result<usize> {
        self.reads += 1;
        match self.reader.read(buf) {
            Ok(n) => {
                self.through += n;
                Ok(n)
            },
            Err(e) => {
                Err(e)
            }
        }
    }
}

```
