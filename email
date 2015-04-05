#!/usr/bin/env python

# The MIT License (MIT)

# Copyright (c) 2015 Eric Zheng

# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:

# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.

# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
# THE SOFTWARE.

import argparse
import smtplib

from email.mime.text import MIMEText

def main(args):
	"""Send an email"""
	message = MIMEText(args.body)
	message['Subject'] = args.subject
	message['From'] = args.sender
	message['To'] = args.to

	server = smtplib.SMTP(args.smtp)
	server.sendmail(args.sender, args.to, message.as_string())
	server.quit()

if __name__ == '__main__':
	parser = argparse.ArgumentParser(description='Send an email.')
	parser.add_argument('--smtp', required=True)
	parser.add_argument('-f', '--from', required=True, dest='sender')
	parser.add_argument('-t', '--to', required=True)
	parser.add_argument('-s', '--subject', default="(no subject)")
	parser.add_argument('-b', '--body', required=True)

	args = parser.parse_args()
	main(args)