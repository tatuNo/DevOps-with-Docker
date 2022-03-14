Ex 3.4 already changed backend base image FROM golang:1.16 to FROM golang:1.16-alpine.
Image ~500MB smaller.

# Before FROM ubuntu:16.04

frontend 530MB

# After FROM node:16-alpine

frontend 416MB