# Thread
Study about Thread

ThreadLocal
------------

![사진1](https://github.com/JUWON-KEVIN-LEE/Thread/blob/master/img/thread_local.png)
<pre><code>
    ThreadLocal<UserInfo> local = new ThreadLocal<UserInfo>(); // 현재 쓰레드와 관련된 로컬 변수를 하나 생성한다.
    
    local.set(currentUser); // 로컬 변수에 값 할당

    UserInfo userInfo = local.get(); // 이후 실행되는 코드는 쓰레드 로컬 변수 값을 사용
</code></pre>

<pre><code>
    public class Context {
        public static ThreadLocal<Date> local = new ThreadLocal<Date>();
    }

    class A {
        public void a() {
            Context.local.set(new Date());
        
            B b = new B();
            b.b();

            Context.local.remove();
        }
    }

    class B {
        public void b() {
            Date date = Context.local.get();

            C c = new C();
            c.c();
        }
    }

    class C {
        public void c() {
            Date date = Context.local.get();
        }
    }
</code></pre>
![사진2](https://github.com/JUWON-KEVIN-LEE/Thread/blob/master/img/thread_local1.png)

[출처 : 자바캔(Java Can Do IT)](http://javacan.tistory.com/entry/ThreadLocalUsage)

<img width="" height=""></img>



