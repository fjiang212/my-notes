http://www.baeldung.com/spring-aop-vs-aspectj

```
package com.example.aop.demo.controlller;

import java.util.Date;

import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import com.example.aop.demo.annotation.Persistable;

@RestController
public class TransactionController {
    @Autowired
    TransactExector exector;

    @RequestMapping("/transaction")
    public String transaction(HttpServletRequest request, HttpServletResponse response) {
        System.out.println("Inside transaction()");
        exector.connect(this, request, response);

        return "Hello user !!! : " + new Date();
    }

    public void transactionInternal(HttpServletRequest request, HttpServletResponse response) {
        System.out.println("Inside transactionInternal()");

    }

    @Component
    public static class TransactExector {
        @Persistable
        public void connect(TransactionController t, HttpServletRequest request, HttpServletResponse response) {
            System.out.println("Inside TransactExector()");
            t.transactionInternal(request, response);

        }
    }
}

```
