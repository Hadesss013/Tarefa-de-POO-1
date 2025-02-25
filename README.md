# Tarefa-de-POO-1
Fernando Franco Tarla
import java.io.IOException;
import java.io.PrintWriter;
import java.time.LocalDateTime;
import java.util.HashSet;
import java.util.Random;
import java.util.Set;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/seu-nome.html")
public class SeuNomeServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html;charset=UTF-8");
        PrintWriter out = response.getWriter();
        out.println("<html><body>");
        out.println("<h1>1290482322004</h1>");
        out.println("<h2>Fernando</h2>");
        out.println("<h2>20 anos</h2>");
        out.println("</body></html>");
    }
}

@WebServlet("/greeting.html")
public class GreetingServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html;charset=UTF-8");
        PrintWriter out = response.getWriter();
        LocalDateTime now = LocalDateTime.now();
        int hour = now.getHour();
        String greeting;
        if (hour >= 5 && hour < 12) {
            greeting = "Bom dia";
        } else if (hour >= 12 && hour < 18) {
            greeting = "Boa tarde";
        } else if (hour >= 18 && hour < 23) {
            greeting = "Boa noite";
        } else {
            greeting = "Vá dormir";
        }
        out.println("<html><body>");
        out.println("<h1>" + greeting + "</h1>");
        out.println("<p>" + now + "</p>");
        out.println("</body></html>");
    }
}

@WebServlet("/random.html")
public class RandomServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html;charset=UTF-8");
        PrintWriter out = response.getWriter();
        Random random = new Random();
        Set<Integer> numbers = new HashSet<>();
        while (numbers.size() < 6) {
            numbers.add(random.nextInt(60) + 1);
        }
        out.println("<html><body>");
        out.println("<h1>Números Aleatórios</h1>");
        out.println("<table border='1'><tr>");
        for (int num : numbers) {
            out.println("<td>" + num + "</td>");
        }
        out.println("</tr></table>");
        out.println("</body></html>");
    }
}

// Página principal
@WebServlet("/index.html")
public class IndexServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html;charset=UTF-8");
        PrintWriter out = response.getWriter();
        out.println("<html><body>");
        out.println("<h1>Bem-vindo</h1>");
        out.println("<ul>");
        out.println("<li><a href='seu-nome.html'>Seu Nome</a></li>");
        out.println("<li><a href='greeting.html'>Saudação</a></li>");
        out.println("<li><a href='random.html'>Números Aleatórios</a></li>");
        out.println("</ul>");
        out.println("</body></html>");
    }
}
