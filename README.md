package lojistapro;

import javax.swing.JOptionPane;

public class LojistaPro2 {

    public static void main(String[] args) {
        
        double faturamento = 0, despesas = 0;
        int vendasContador = 0;
        int opcao = -1;

        JOptionPane.showMessageDialog(null, "=== BEM-VINDO AO LOJISTA PRO 2.0 ===");

        while (opcao != 0) {
            
            String menu = "--- MENU LOJISTA PRO ---\n\n"
                        + "1. Lançar Venda\n"
                        + "2. Registrar Boleto\n"
                        + "3. Fechamento de Caixa\n"
                        + "4. Imposto (6%)\n"
                        + "0. Sair\n\n"
                        + "Escolha uma opção:";
            
            String entrada = JOptionPane.showInputDialog(null, menu);
            
            if (entrada == null) break;

            opcao = Integer.parseInt(entrada);

            if (opcao == 1) {
                String valorVenda = JOptionPane.showInputDialog("Valor da venda: R$");
                if (valorVenda != null) {
                    faturamento += Double.parseDouble(valorVenda.replace(",", "."));
                    vendasContador++;
                    JOptionPane.showMessageDialog(null, "✅ Venda registrada!");
                }

            } else if (opcao == 2) {
                String valorDespesa = JOptionPane.showInputDialog("Valor da despesa: R$");
                if (valorDespesa != null) {
                    despesas += Double.parseDouble(valorDespesa.replace(",", "."));
                    JOptionPane.showMessageDialog(null, "⚠️ Despesa anotada!");
                }

            } else if (opcao == 3) {
                String relatorio = String.format(
                    "--- RESUMO DE CAIXA ---\n\nVendas: %d\nFaturamento: R$ %.2f\nDespesas: R$ %.2f\n\nSALDO LÍQUIDO: R$ %.2f",
                    vendasContador, faturamento, despesas, (faturamento - despesas)
                );
                JOptionPane.showMessageDialog(null, relatorio);

            } else if (opcao == 4) {
                double imposto = faturamento * 0.06;
                JOptionPane.showMessageDialog(null, String.format("Imposto Estimado (6%%): R$ %.2f", imposto));

            } else if (opcao == 0) {
                JOptionPane.showMessageDialog(null, "Saindo do Lojista Pro 2.0...");
            } else {
                JOptionPane.showMessageDialog(null, "❌ Opção Inválida!");
            }
        }
    }
}

